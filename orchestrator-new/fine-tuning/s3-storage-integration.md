# Интеграция с S3-хранилищем

Для хранения файлов скринов, передаваемых роботами вместе с логами (**RobotLogs**), и архивов дистрибутивов роботов и агентов (**WebApi**) имеется возможность сконфигурировать службы RobotLogs и WebApi 
для использования S3-хранилища (Minio).

В службе **RobotLogs** в секцию *ScreenFileUpload* требуется добавить параметры: 

![](../../orchestrator-new/resources/fine-tuning/s3-storage-integration1.PNG)

В службе **WebApi** требуется добавить секцию *FileStore*:

![](../../orchestrator-new/resources/fine-tuning/s3-storage-integration2.PNG)

### Описание параметров подключения к S3 в ScreenFileUpload/FileStore

| №п/п | Наименование параметра | Назначение | Примечание |
| --- | --- | --- | --- |
| 1. | StoreType/Type | 0 – файловое хранилище,1 – S3 (minio) |  |
| 2. | Minio.Endpoint | Адрес конечной точки minio |  |
| 3. | Minio.AccessKey | Параметры доступа. Настраиваются администратором minio (см. рисунок ниже) |  |
| 4. | Minio.SecretKey |  | Должен быть зашифрован утилитой шифрования |
| 5. | Minio.SSL | Устанавливается в true, если minio настроен на использование https |  |

### Параметры подключения к minio:

![](../../orchestrator-new/resources/fine-tuning/s3-storage-integration3.PNG)
