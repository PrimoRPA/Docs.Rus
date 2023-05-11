# Установка Nginx
Раздел содержит инструкцию по установке **Nginx** под Windows 2016 Server. 

**Nginx** используется как реверс-прокси для WebApi и как стандартный веб-сервер для отдачи статических файлов UI Оркестратора. Nginx настраивается при помощи файла nginx.config, который идет в комплекте поставки. Работа приложения по https также настраивается в nginx.config. Файлы SSL-сертификата (самоподписанный, невалидный) входят в комплект поставки.  

**Как установить Nginx:**

1\. Распакуйте архив `C:\Install\nginx-1.21.1.zip` в папку `C:\Primo\nginx-1.21.1`.\
2\. Перейдите в папку `C:\Primo\nginx-1.21.1`

Если для приема логов роботов не используется внешний сервис RobotLogs, удалите из конфига nginx.conf проксирование в RobotLogs: 

![](<../../../.gitbook/assets/install-nginx-win-1.png>)

![](<../../../.gitbook/assets/install-nginx-win-2.png>)

3\.	При помощи cmd запустите nginx:
*	Перейдите в папку с установленным nginx: 
```
cd C:\Primo\nginx-1.21.1
```
* Выполните команду запуска: 
```
start nginx
```
* Убедитесь, что nginx запущен, выполнив команду:
``` 
tasklist /fi "imagename eq nginx.exe" 
```
![](<../../../.gitbook/assets/install-nginx-win-3.png>)

4\.	После каждой перезагрузки Windows требуется вручную запускать nginx. Чтобы этого не делать каждый раз, приложение nginx следует поставить в автозагрузку: 
* Создайте bat-файл `C:\orch_start.bat` со следующими командами: 
```
cd C:\Primo\nginx-1.21.1 
start nginx 
```
* Внесите созданный файл в автозагрузку Windows командой:
```
> REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v orch_start /t REG_SZ /d "C:\orch_start.bat"
```
Добавится соответствующее значение в системный реестр:

![](<../../../.gitbook/assets/install-nginx-win-4.png>)

5\. Откройте порт 44392 на файерволе. В PowerShell выполните команду:
```
> New-NetFirewallRule -DisplayName 'Primo Orchestrator (44392)' -Profile 'Private, Domain, Public' -Direction Inbound -Action Allow -Protocol TCP -LocalPort 44392
```
6\. При необходимости можно перезапустить nginx:
```
>nginx -s reload
```

:white_check_mark: **Готово**: приложение Nginx успешно установлено и добавлено в автозагрузку Windows.
