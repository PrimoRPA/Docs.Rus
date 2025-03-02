# Секционирование существующих таблиц с журналом Робота и Оркестратора для SQLServer - Вариант с фиксированной схемой секционирования

## Создание файловых групп

Для секционирования по месяцам необходимо создать файловые группы на каждый месяц. 
```
ALTER DATABASE ltoolslogs ADD FILEGROUP logs01;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs02;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs03;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs04;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs05;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs06;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs07;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs08;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs09;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs10;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs11;
ALTER DATABASE ltoolslogs ADD FILEGROUP logs12;
```
Подключаем к каждой группе файл хранилища. Путь к файлам .NDF зависит от конфигурации SQLServer’а, может быть, например таким, `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA`.
```
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs01, FILENAME = '<file-groups-path>\logs01.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs01;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs02, FILENAME = '<file-groups-path>\logs02.ndf',
	SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs02;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs03, FILENAME = '<file-groups-path>\logs03.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs03;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs04, FILENAME = '<file-groups-path>\logs04.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs04;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs05, FILENAME = '<file-groups-path>\logs05.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs05;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs06, FILENAME = '<file-groups-path>\logs06.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs06;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs07, FILENAME = '<file-groups-path>\logs07.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs07;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs08, FILENAME = '<file-groups-path>\logs08.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs08;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs09, FILENAME = '<file-groups-path>\logs09.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs09;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs10, FILENAME = '<file-groups-path>\logs10.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs10;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs11, FILENAME = '<file-groups-path>\logs11.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs11;
ALTER DATABASE ltoolslogs ADD FILE (
    NAME = logs12, FILENAME = '<file-groups-path>\logs12.ndf',
    SIZE = 10 MB, MAXSIZE = UNLIMITED, FILEGROWTH = 1024 KB
) TO FILEGROUP logs12;
Создание функции секционирования
CREATE PARTITION FUNCTION LogsPartitionFunction(int)
AS RANGE RIGHT FOR VALUES (2,3,4,5,6,7,8,9,10,11,12);
```

## Создание функции секционирования

```
CREATE PARTITION FUNCTION LogsPartitionFunction(int)
AS RANGE RIGHT FOR VALUES (2,3,4,5,6,7,8,9,10,11,12);
```
Внимание! Здесь создаются не секции, а границы между секциями, поэтому количество возвращаемых значений у функциии на 1 меньше чем секций.

## Создание схемы секционирования

```
CREATE PARTITION SCHEME LogsPartitionScheme
AS PARTITION LogsPartitionFunction
TO (
'logs01', 'logs02', 'logs03', 'logs04', 'logs05', 'logs06', 
'logs07', 'logs08', 'logs09', 'logs10', 'logs11', 'logs12');
```

## Настройка таблицы Logs

Добавляем вычисляемую колонку для секционирования
```
ALTER TABLE Logs ADD PartitionColumn as MONTH(OrchTimestampUtc) PERSISTED;
```
Создаём индекс для партиционирования
```
CREATE NONCLUSTERED INDEX IX_Logs_Partition ON [Logs] ([PartitionColumn]) ON [LogsPartitionScheme]([PartitionColumn]);
```

## Настройка таблицы OrchEvents

Добавляем вычисляемую колонку для секционирования
```
ALTER TABLE OrchEvents ADD PartitionColumn as MONTH(OrchTimestampUtc) PERSISTED;
```
Создаём индекс для партиционирования
```
CREATE NONCLUSTERED INDEX IX_OrchEvents_Partition ON [Logs] ([PartitionColumn]) ON [LogsPartitionScheme]([PartitionColumn]);
```



