# Предварительная настройка машины Оркестратора
Раздел содержит инструкцию по предварительной настройке машины Оркестратора под Windows 2016 Server.\
Процесс состоит из нескольких шагов:

**Шаг 1. Копирование дистрибутивов из комплекта поставки**

Создайте папку, в которую будут скопированы дистрибутивы из комплекта поставки: 
```
> mkdir C:\Install
```
В созданную папку скопируйте дистрибутивы из комплекта поставки:
```
WebApi.zip
WebApi-IIS.zip
States.zip
Notifications.zip
nginx-1.21.1.zip
UI.zip
aspnetcore-runtime-3.1.15-win-x64.exe
dotnet-hosting-3.1.15-win.exe
rewrite_amd64_en-US.msi
ARRv3_0.exe
rabbitmq.zip
PrimoOrchestrator.ps1
PrimoOrchestrator-IIS.ps1
PowerShell-7.1.3-win-x64.msi
ChromeStandaloneSetup64.exe
PasswordEncryptor.zip
grafana-8.0.6.windows-amd64.msi
```

**Шаг 2. Установка PowerShell 7.1.3**

Произведите установку PowerShell в соответствии с инструкцией [Установка PowerShell-7.1.3 под Windows](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/windows/powershell-install). PowerShell будет использоваться далее при настройке Оркестратора.

**Шаг 3. Установка браузера Google Chrome**

Google Chrome нужен для проверки работоспособности компонентов Оркестратора.\
Браузер устанавливается из `C:\Install\ChromeStandaloneSetup64.exe`, который идет с комплектом поставки.

**Шаг 4. Создание папки для служб Оркестратора**

Создайте папку C:\Primo: 
```
> mkdir C:\Primo
```
В папку `C:\Primo` в дальнейшем будут устанавливаться службы Оркестратора.

