# Приложение. Установка агента Оркестратора без инсталлятора
Раздел предназначен для опытных пользователей и содержит инструкцию по тонкой настройке машины робота. 

## Установка PowerShell Core
Производим установку в соответствии с инструкцией «Руководство по установке PowerShell-7.1.3 под Windows.docx» из комплекта поставки.

## Установка агента Оркестратора
Создаем переменную окружения из PowerShell:
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Проверить настройку переменных можно через System Properties/Advanced ➝ Environment Variables:

![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

Копируем файлы из дистрибутива Агента через PowerShell:
>$InstallPath = "C:\Install" 
>Expand-Archive -LiteralPath "$InstallPath\Agent.zip" -DestinationPath 'C:\Primo\Agent'
	Проверяем, что файлы скопировались в папку C:\Primo\Agent:
  
![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

Создаем службу из PowerShell (рисунок 17):
>New-Service -Name "Primo.Orchestrator.Agent" -BinaryPathName "C:\Primo\Agent\Primo.Orchestrator.Agent.exe" -Description "Primo.Orchestrator.Agent" -DisplayName "Primo.Orchestrator.Agent" -StartupType Automatic

![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

Редактируем конфигурационный файл C:\Primo\Agent\appsettings.ProdWin.json – указываем IP-адрес Оркестратора, TenantId Агента (рисунок 18) и пользователя из тенанта . Для дефолтного тенанта null.

```json

```

Запускаем службу (рисунок 19). Служба должна работать под Local System account 
(рисунок 20).

![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

![](<../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

## Настройка брандмауэра Windows
Открываем порты для http-сервера Агента (5002) и Роботов (8000-9000) – по этим портам к ним обращается сервер Оркестратора.
В PowerSchell выполняем команды:
>New-NetFirewallRule -Name "Primo Agent (5002)" -DisplayName "Primo Agent (5002)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 5002

>New-NetFirewallRule -Name "Primo Robot (8000-9000)" -DisplayName "Primo Robot (8000-9000)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 8000-9000

## Проверка настройки машины Робота
Проверяем, что сервис Агента (Primo.Agent) запущен






