#  Primo RPA Studio 1.24.6.17 

Изменения для версии приложения **Primo RPA Studio Windows 1.24.6.17**

### Обновления и улучшения 


1. Добавлено новое свойство `Точное совпадение колонок` в элемент **Вставка данных (WFInsert)**
   - При включенном свойстве импортируются все колонки из DataTable, и если в таблице есть колонки, которых нет в базе данных, возникает ошибка.
   - При выключенном свойстве импортируются только те колонки, которые совпадают по именам с колонками в базе данных.

2. Улучшен процесс импорта данных из DataTable в базу данных. Увеличена скорость загрузки больших таблиц примерно в 2 раза за счет объединения всех операций вставки (Insert) в одну транзакцию.

3. Исправлена ошибка, при которой кнопка **Приостановить отладку** не срабатывала. Теперь отладка корректно приостанавливается на выбранном элементе.

## Где найти

[**Скачать Primo RPA Studio**](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FStudio)


[**Скачать Primo RPA Robot**](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot). 