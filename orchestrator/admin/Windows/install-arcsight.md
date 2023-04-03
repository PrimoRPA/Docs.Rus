# Установка ArcSight как службы

Раздел содержит инструкцию по установке ArcSight как службы под Windows 2016 Server. В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена, поэтому ArcSight можно устанавливать сразу. 

Как это сделать:

1. Разархивируйте `C:\Install\ArcSight.zip` в `C:\Primo\ArcSight`. Например, при помощи PowerShell:

```
$InstallPath = "C:\Install"
Expand-Archive -LiteralPath "$InstallPath\ArcSight.zip" -DestinationPath "C:\Primo\ArcSight " -Force
```

2\. Создайте системную переменную окружения. Для этого в PoweShell запустите команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

3\. Настройте уровни логирования приложения (Information, Warning, Error):

![](<../../../.gitbook/assets/install-arcsight-1.png>)

4\. Настройте путь до папки с логами приложения и шаблон имени файлов логов:

![](<../../../.gitbook/assets/install-arcsight-2.png>)

5\. Настройте параметры интеграции с ArcSight:

![](<../../../.gitbook/assets/install-arcsight-3.png>)

**Описание параметров интеграции с ArcSight:**
* Секция Device:
  * **Vendor**. Тип: String. Рекомендуемое значение: `Primo`. Описание: по спецификации ArcSight.
  * **Product**. Тип: String. Рекомендуемое значение: `Orchestrator.ArcSight`. Описание: по спецификации ArcSight.
  * **Version**. Тип: String. Рекомендуемое значение: `1.0.0.0`. Описание: по спецификации ArcSight.
* Секция CEF:
  * **Version**. Тип: String. Рекомендуемое значение: `0`. Описание: по спецификации ArcSight.
* Секция Files:
  * **Path**. Тип: String. Рекомендуемое значение: `C:\\Primo\\ArcSight\\IntegrationLogs\\ArcSight-.txt`. Описание: папка, из которой ArcSight будет забирать логи и префикс имени файла логов. Например, ArcSight-20220521.txt, ArcSight-20220521 1.txt, ArcSight-20220521 2.txt. Нумерация, 1, 2 и т. д. для одной даты. См. пункт ниже, про параметр MaxCountEvents.
  * **MaxCountEvents**. Тип: Int. Рекомендуемое значение: `2000`. Описание: максимальное количество строк в одном файле логов. После этого значения создается новый файл. Для нового файла для одной даты используется автоматическая нумерация. **Должно быть согласовано с механизмом чтения файлов из папки обмена ArcSight.**
  * **MaxCountFiles**. Тип: Int. Рекомендуемое значение: `200`. Описание: максимальное количество файлов в папке обмена. Старые файлы логов удаляются. **Должно быть согласовано с механизмом чтения файлов из папки обмена ArcSight.**
  * **DateFormat**. Тип: String. Рекомендуемое значение: `yyyyMMddHH`. Описание: формат даты в постфиксе имени файла.
* Секция Queue:
  * **ConvertThreadSleep**. Тип: Int. Рекомендуемое значение: `2000`. Описание: время (миллисекунды) засыпания потока обработки входной очереди событий для их сопоставления формату ArcSight.
  * **WriteFileThreadSleep**. Тип: Int. Рекомендуемое значение: `2000`. Описание: время (миллисекунды) засыпания потока записи событий в папку обмена. **Должно быть согласовано с механизмом чтения файлов из папки обмена ArcSight**.
  * **BatchReadEventsCount**. Тип: Int. Рекомендуемое значение: `1000`. Описание: максимальное количество событий, считываемых из входной очереди за один раз. Считанные события обрабатываются и помещаются в выходную очередь.
  * **BatchReadResultEventsCount**. Тип: Int. Рекомендуемое значение: `1000`. Описание: максимальное количество событий, считываемых из выходной очереди за один раз. Считанные события конвертируются в строки ArcSight и записываются в файлы в папке обмена.


Регистрируем **Primo.Orchestrator.ArcSight.exe** как службу Windows и сразу запускаем её. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:

```
$secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
$mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\LOCAL SERVICE', $secpasswd)  
New-Service -Name Primo.Orchestrator.ArcSight -BinaryPathName "C:\Primo\ArcSight\Primo.Orchestrator.ArcSight.exe" -Credential $mycreds -Description "Primo.Orchestrator.ArcSight " -DisplayName "Primo.Orchestrator.ArcSight " -StartupType Automatic 
$s = Get-Service "Primo.Orchestrator.ArcSight"
$s.Start()
```
Пароль в `$secpasswd` можно задать любой.

После этого созданная служба Primo.Orchestrator.ArcSight будет отображаться в списке всех служб как запущенная:

![](<../../../.gitbook/assets/install-arcsight-4.png>)

![](<../../../.gitbook/assets/install-arcsight-5.png>)

После установки ArcSight требуется настройка интеграционного шлюза LogEventsWebhook.
