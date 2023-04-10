# Установка TimescaleDB
Расширение для базы данных PostgreSQL 12 – TimescaleDB – используется в Оркестраторе для Logs DB. Раздел содержит инструкцию по установке TimescaleDB под Windows 2016 Server. 

**Как установить TimescaleDB:**

1\. Проверяем, что в системной переменной окружения **Path** установлен путь до соответствующей версии PostgreSQL.

:yellow_circle: ***Если путь отсутствует, добавьте его вручную.***

![](<../../../.gitbook/assets/install-timescale-1.png>)

Диалог редактирования переменной окружения:

![](<../../../.gitbook/assets/install-timescale-2.png>)


2\. Далее распакуем архив `C:\Install\timescaledb-postgresql-12_1.7.4-windows-amd64.zip` в папку `C:\Install`.\
3\.	Из папки `timescaledb` запускаем установочный файл `setup.exe` от имени Администратора:

![](<../../../.gitbook/assets/install-timescale-3.png>)

4\. Выбираем **Да** в окне разрешения на установку приложения:

![](<../../../.gitbook/assets/install-timescale-4.png>)

5\. Для начала установки выбираем на клавиатуре латинскую букву `y` и жмем `Enter`:

![](<../../../.gitbook/assets/install-timescale-5.png>)

6\. Указываем полный путь к файлу конфигурации `C:\Primo\PostgreSQL\Data\postgresql.conf` и жмем `Enter`:

![](<../../../.gitbook/assets/install-timescale-6.png>)

7\. В последующих шагах принимаем все настройки по умолчанию и вводим латинскую букву `y`:

![](<../../../.gitbook/assets/install-timescale-7.png>)

8\.

![](<../../../.gitbook/assets/install-timescale-8.png>)

9\.

![](<../../../.gitbook/assets/install-timescale-9.png>)

10\. 

![](<../../../.gitbook/assets/install-timescale-10.png>)

11\.

![](<../../../.gitbook/assets/install-timescale-11.png>)

12\.

![](<../../../.gitbook/assets/install-timescale-12.png>)

13\. На этом шаге вы должны увидеть уведомление об успешной установке:

![](<../../../.gitbook/assets/install-timescale-13.png>)

Нажмите `Enter` для закрытия окна терминала.

:white_check_mark: **Готово**: расширение TimescaleDB успешно установлено.
