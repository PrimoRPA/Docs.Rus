---
description: Execute query (SAP HANA)
---

# Выполнить запрос (SAP HANA)

  ![](<../../../.gitbook/assets1/execute_hana_sap.png>)


Компонент выполняет запрос к базе данных SAP HANA. Ожидание результатов предполагает, что запрос должен вернуть данные.

## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет [Primo.Sap.Data.Hana](https://www.nuget.org/packages/Primo.Sap.Data.Hana), иначе данный элемент будет недоступен.  
Также необходимо предварительно установить клиент SAP HANA, который можно скачать с [официального сайта SAP HANA](https://tools.hana.ondemand.com/#hanatools).

## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**База данных:**
1. *Соединение с БД\* *[Primo.Sap.Data.Hana.DatabaseInst] — экземпляр соединения с базой данных.
1. *Строка соединения\* *[String] — строка подключения к базе данных (например, SERVER=<hostname>:<port>; DATABASE=<database name>; UID=<username>; PWD=<password>).

**Вывод:**
1. Кол-во [Int32] — количество обработанных строк.
1. Переменная (массив) [List\<List\<string\>\>] — переменная для сохранения результатов запроса в виде массива.
1. Переменная (таблица) [System.Data.DataTable] — переменная для сохранения результатов запроса в виде таблицы.

**Данные запроса:**
1. Аргументы (конструктор) [String] — аргументы запроса в виде строки.
1. Аргументы (массив) [List\<Primo.Sap.Data.Hana.Model.ArgumentsModelItem\>] — массив аргументов.
1. Наличие результатов [Boolean] — признак ожидания результатов запроса.
1. Таймаут\* [Int32] — максимальное время ожидания выполнения запроса, в миллисекундах. Значение по умолчанию: 10000.
1. Текст запроса\* [String] — текст SQL-запроса для выполнения.



#### Структура аргумента
Каждый аргумент в массиве включает:
- *Position* (int) — порядковый номер.
- *Name* (String) — название.
- *Value* (Object) — значение.

#### Пример:

```csharp
new Primo.Database.SqlServer.Model.ArgumentsModelItem { Position = 1, Name = "Param1", Value = 123 }
```
