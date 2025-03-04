# Секционирование существующих таблиц с журналом Робота и Оркестратора для SQLServer

## Создание файловых групп

Для секционирования по месяцам необходимо создать файловые группы на каждый месяц. Приведены примеры до конца текущего года, в дальнейшем состав групп можно расширять.

```
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202304
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202305
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202306
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202307
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202308
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202309
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202310
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202311
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202312
GO
ALTER DATABASE ltoolslogs
ADD FILEGROUP logs202401
GO
```
Подключаем к каждой группе файл хранилища. Путь к файлам .NDF зависит от конфигурации SQLServer’а, может быть, например таким, `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA`.
```
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202304,
    FILENAME = '<file-groups-path>\logs202304.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202304;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202305,
    FILENAME = '<file-groups-path>\logs202305.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202305;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202306,
    FILENAME = '<file-groups-path>\logs202306.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202306;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202307,
    FILENAME = '<file-groups-path>\logs202307.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202307;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202308,
    FILENAME = '<file-groups-path>\logs202308.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202308;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202309,
    FILENAME = '<file-groups-path>\logs202309.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202309;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202310,
    FILENAME = '<file-groups-path>\logs202310.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202310;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202311,
    FILENAME = '<file-groups-path>\logs202311.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202311;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202312,
    FILENAME = '<file-groups-path>\logs202312.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202312;
GO
ALTER DATABASE ltoolslogs    
ADD FILE (
    NAME = logs202401,
    FILENAME = '<file-groups-path>\logs202401.ndf',
    SIZE = 10 MB, 
    MAXSIZE = UNLIMITED, 
    FILEGROWTH = 1024 KB
) TO FILEGROUP logs202401;
GO
```

## Создание функции секционирования

```
CREATE PARTITION FUNCTION LogsPartitionFunction(datetime2(7))
AS RANGE RIGHT
FOR VALUES (
'2023-04-01 00:00:00.0000000', '2023-05-01 00:00:00.0000000', '2023-06-01 00:00:00.0000000',
'2023-07-01 00:00:00.0000000', '2023-08-01 00:00:00.0000000', '2023-09-01 00:00:00.0000000',
'2023-10-01 00:00:00.0000000', '2023-11-01 00:00:00.0000000', '2023-12-01 00:00:00.0000000',
'2024-01-01 00:00:00.0000000'
);
GO
```

## Создание схемы секционирования

```
CREATE PARTITION SCHEME LogsPartitionScheme
AS PARTITION LogsPartitionFunction
TO ('Primary',
'logs202304', 'logs202305', 'logs202306', 'logs202307',
'logs202308', 'logs202309', 'logs202310', 'logs202311',
'logs202312', 'logs202401'
)
GO
```

## Настройка таблицы Logs

Удаляем основной кластерный индекс
```
ALTER TABLE [Logs]
DROP CONSTRAINT [PK_Logs]
GO
```
Создаём такой же, но не кластерный
```
ALTER TABLE [Logs]
ADD CONSTRAINT PK_Logs PRIMARY KEY NONCLUSTERED([Id] ASC) 
ON [PRIMARY]
GO
```
Создаём кластерный индекс для секционирования
```
CREATE CLUSTERED INDEX IX_Logs_OrchTimestampUtc
ON [Logs] ([OrchTimestampUtc] ) 
ON [LogsPartitionScheme]([OrchTimestampUtc])
GO
```

## Настройка таблицы OrchEvents

Удаляем основной кластерный индекс
```
ALTER TABLE [OrchEvents]
DROP CONSTRAINT [PK_OrchEvents]
GO
```
Создаём такой же, но не кластерный
```
ALTER TABLE [OrchEvents]
ADD CONSTRAINT PK_OrchEvents PRIMARY KEY NONCLUSTERED([Id] ASC) 
ON [PRIMARY]
GO
```
Удаляем основной кластерный индекс по колонке OrchTimestampUtc
```
DROP INDEX [OrchEvents].IX_OrchEvents_AllOrchTimestampUtc
GO
DROP STATISTICS [OrchEvents].IX_OrchEvents_AllOrchTimestampUtc
GO
```
Создаём кластерный индекс для секционирования
```
CREATE CLUSTERED INDEX IX_OrchEvents_AllOrchTimestampUtc
ON [OrchEvents]([OrchTimestampUtc]) 
ON [LogsPartitionScheme]([OrchTimestampUtc])
GO
```

