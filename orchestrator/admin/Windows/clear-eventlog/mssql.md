# Настройка автоматической очистки событий Оркестратора для MSSQL

Разверните узел Агент SQL Server, откройте контекстное меню узла **Задания** и выберите **Управление расписаниями**:

![](<../../../../.gitbook/assets/1. MSSQL Управление расписаниями.png>)

В диалоговом окне **Управление расписаниями** выберите **Создать**:

![](<../../../../.gitbook/assets/2. MSSQL Создать.png>)

В поле **Имя** введите имя нового расписания - **Каждые 30 минут**.\
Тип расписания - **Повторяющееся задание**. Задание будет выполняться ежедневно каждые 30 минут.\
Если не нужно, чтобы расписание вступило в силу немедленно после создания, снимите флажок **Включено**:

![](<../../../../.gitbook/assets/MSSQL. Очистка событий. Свойства расписания.png>)


Создаем хранимую процедуру:

```TSQL
USE ltoolslogs;

CREATE PROC truncate_logs(
    @last_minutes INTEGER, 
    @max_database_size INTEGER)  
AS 
BEGIN
    DECLARE @database_size INTEGER;  
	SET @database_size = (SELECT total_size_mb = SUM(size)
                          FROM sys.master_files WITH(NOWAIT)
                          WHERE database_id = DB_ID() 
                          GROUP BY database_id);
    IF (@database_size > @max_database_size) BEGIN
       EXEC msdb.dbo.sp_delete_database_backuphistory @database_name = 'ltoolslogs';
       DELETE FROM OrchEvents 
       WHERE OrchTimestampUtc < DATEADD(mi, -@last_minutes, GETUTCDATE());
    END;
END;
```

Создаем задание, которое будет запускать эту хранимую процедуру по расписанию:

![](<../../../../.gitbook/assets/MSSQL. Очистка событий. Создать задание.png>)

Вводим общие параметры задания:
* Имя - **Очистка журнала событий**; 
* Описание - **В БД ltoolslogs при достижении максимального размера БД в таблице OrchEvents удаляются старые записи - старше чем 30 минут**

![](<../../../../.gitbook/assets/4. MSSQL Создание задания с процедурой.png>)

Задаем шаги задания: будет один шаг с именем шага **truncate_logs** и командой:
```
USE ltoolslogs;
EXEC truncate_logs  @last_minutes=30, @max_database_size=524288000;
```

![](<../../../../.gitbook/assets/6. MSSQL Шаги задания.png>)

Задаем расписание. Чтобы выбрать готовое, нажимаем кнопку **Выбрать**:
  
![](<../../../../.gitbook/assets/7. MSSQL Расписание параметры.png>)

Откроется список расписаний:
  
![](<../../../../.gitbook/assets/8. MSSQL Выбор расписания для задания.png>)

Выбираем ранее созданное расписание **Каждые 30 минут**:
  
![](<../../../../.gitbook/assets/9. MSSQL Выбор-2.png>)

Нажимаем **ОК**. Задание **Очистка журнала событий** будет отображаться среди всех заданий:
  
![](<../../../../.gitbook/assets/10. MSSQL Отображение задания.png>)

