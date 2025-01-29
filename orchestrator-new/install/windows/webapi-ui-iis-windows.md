# Установка WebApi и UI на IIS под Windows 2016 Server

:small_orange_diamond: Перед началом работы установите все последние обновления Windows.

### 1. Включение компьютера в AD 
(не требуется, если используется DHCP)

Перед установкой IIS настройте статический IP адрес и DNS. В DNS пропишите IP контроллера AD. Это нужно для включения компьютера в AD.

Правой кнопкой мыши щелкните по иконке «Network» в правом нижнем углу:

![](../../../orchestrator-new/resources/install/windows/iis-1-networkicon.PNG)

Во всплывающем меню выберите «Open Network and Sharing Center»:

![](../../../orchestrator-new/resources/install/windows/iis-2-popupwindow.PNG)

В открывшемся окне «Network and Sharing Center» в левом меню выберите «Change adapter settings»:

![](../../../orchestrator-new/resources/install/windows/iis-3-changeadapter.PNG)

В открывшемся окне «Network Connections» выберите сетевой адаптер и щелкните по нему правой кнопкой мыши:

![](../../../orchestrator-new/resources/install/windows/iis-4-networkconnections.PNG)

Во всплывающем меню выберите «Properties»:

![](../../../orchestrator-new/resources/install/windows/iis-5-properties.PNG)

В открывшемся окне «Ethernet Properties» щелкните по «Internet Protocol Version 4 (NCP/IPv4)»:

![](../../../orchestrator-new/resources/install/windows/iis-6-ethernetproperties.PNG)

В открывшемся окне «Internet Protocol Version 4 (NCP/IPv4) Properties» (рисунок 7) настройте параметры:

![](../../../orchestrator-new/resources/install/windows/iis-7-ipvproperties.PNG)

Выберите «Use the following IP address» и пропишите значения полей «IP address», «Subnet mask» и «Default gateway». 
> Для VM значения этих полей можно узнать командой ipconfig

Выберите «Use the following DNS server addresses» и пропишите в поле «Preferred DNS server» IP контроллера домена.

Для удобства дальнейших настроек поменяйте имя компьютера, например, на «IIS». В главном меню Windows выберите пункт «Settings»:

![](../../../orchestrator-new/resources/install/windows/iis-8-winsettings.PNG)

В открывшемся окне «Settings» выберите пункт меню «System»:

![](../../../orchestrator-new/resources/install/windows/iis-9-settingssystem.PNG)

И потом «About»:

![](../../../orchestrator-new/resources/install/windows/iis-10-settingssystemabout.PNG)

При помощи кнопки «Rename PC» переименуйте компьютер, дождитесь перезагрузки.

Здесь же присоедините компьютер к AD:

![](../../../orchestrator-new/resources/install/windows/iis-11-joindomain.PNG)

Нажмите кнопку «Join a domain» и выберите имя AD:

![](../../../orchestrator-new/resources/install/windows/iis-12-domainname.PNG)

Нажмите кнопку «Next» и введите логин/пароль доменной учетной записи:

![](../../../orchestrator-new/resources/install/windows/iis-13-domainloginpw.PNG)

Добавьте информацию о доменной учетной записи на компьютер, выбрав «Account type» = «Administrator»:

![](../../../orchestrator-new/resources/install/windows/iis-14-domainaddacc.PNG)

Перезагрузите компьютер:

![](../../../orchestrator-new/resources/install/windows/iis-15-domainrestartpc.PNG)

После перезагрузки компьютера появится возможность входа в AD с доменной учетной записью:

![](../../../orchestrator-new/resources/install/windows/iis-16-primosignin.PNG)

## 2. Установка IIS

Войдите в систему с локальной учетной записью Administrator:

![](../../../orchestrator-new/resources/install/windows/iis-17-iisadmin.PNG)

В «Server Manager» (откроется автоматически после входа в систему, также его можно запустить из главного меню), выберите «Add Roles and Features»:

![](../../../orchestrator-new/resources/install/windows/iis-18-addroles.PNG)

В «Before you begin» нажмите кнопку «Next»:

![](../../../orchestrator-new/resources/install/windows/iis-19-addrolesbegin.PNG)

В «Installation Type» оставьте выбор по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-20-addrolesinstalltype.PNG)

В «Server Selection» оставьте по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-21-addrolesserversel.PNG)

В «Server Roles» выберите «Web Server (IIS)»:

![](../../../orchestrator-new/resources/install/windows/iis-22-addroles-roles.PNG)

В «Features» оставьте выбор по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-23-addroles-features.PNG)

В «Web Server Role (IIS)» нажмите кнопку «Next»:

![](../../../orchestrator-new/resources/install/windows/iis-24-addroles-webserver.PNG)

В «Role Services» выберите «HTTP Redirection» и «Windows Authentication»:

![](../../../orchestrator-new/resources/install/windows/iis-25-addroles-roleservices.PNG)

:small_orange_diamond: «WebDAV Publishing» выбирать нельзя. Если он выбран ранее – требуется его отключить, сняв галку.

В «Confirmation» нажмите кнопку «Install» и дождитесь завершения установки:

![](../../../orchestrator-new/resources/install/windows/iis-26-addroles-confirm.PNG)

### 3. Разворачивание узлов веб-приложения

Откройте оснастку для управления IIS:

![](../../../orchestrator-new/resources/install/windows/iis-27-iismngmnt.PNG)

Создайте системную переменную окружения ASPNETCORE_ENVIRONMENT= ProdWin. Для этого в PoweShell выполните команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Для узла WebApi создайте отдельный неуправляемый Application Pool с наименованием Primo.WebApi, 
**Start Mode = AlwaysRunning и Regular Time Interval (minutes) = 0** (чтобы пулл приложений не выгружался, так как при выгрузке сломается работа фоновых служб приложения).

Добавление Application Pool:

![](../../../orchestrator-new/resources/install/windows/iis-28-apppool.PNG)

Параметры Application Pool:

![](../../../orchestrator-new/resources/install/windows/iis-29-apppool-param1.PNG)

![](../../../orchestrator-new/resources/install/windows/iis-29-apppool-param2.PNG)

Добавлен Application Pool с наименованием Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-30-apppool-primo.PNG)

Создайте папки `C:\Primo\UI` и `C:\Primo\WebApi`, в которые разархивируйте UI.zip и 
WebApi-IIS.zip из комплекта поставки.

Рабочий каталог узла UI:

![](../../../orchestrator-new/resources/install/windows/iis-31-node-ui.PNG)

Рабочий каталог узла WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-32-node-webapi.PNG)

Добавьте веб-узел Primo.WebApi, установите для него ранее созданный Application Pool с наименованием Primo.WebApi.

Добавление веб-узла Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-33-addwebsite-primo.PNG)

Параметры веб-узла Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-34-primowebsite-param.PNG)

Добавлен веб-узел Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-35-websiteadded.PNG)

Чтобы Primo.WebApi заработал под IIS, установите `dotnet-hosting-7.0.11-win.exe` 
(https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-7.0.11-windows-hosting-bundle-installer)
из комплекта поставки и перезагрузите компьютер.

Для создания узла UI сначала создайте для веб-сервера SSL-сертификат , так как этот узел будет работать по https.

> Для промышленного узла необходимо использовать SSL-сертификат, выданный доверенным удостоверяющим центром.

Открытие оснастки управления сертификатами:

![](../../../orchestrator-new/resources/install/windows/iis-36-certmngmnt.PNG)

Добавление самоподписанного SSL-сертификата:

![](../../../orchestrator-new/resources/install/windows/iis-37-add-sslcert.PNG)

Параметры SSL-сертификата:

![](../../../orchestrator-new/resources/install/windows/iis-38-sslcert-params.PNG)

SSL-сертификат с наименованием Primo установлен:

![](../../../orchestrator-new/resources/install/windows/iis-39-sslcert-added.PNG)

Добавьте веб-узел Primo.UI, установите для него Application Pool с наименованием DefaultAppPool и выберите ранее созданный SSL-сертификат с наименованием Primo: 

![](../../../orchestrator-new/resources/install/windows/iis-40-primosite-params.PNG)

На этом шаге узлы Primo.WebApi и Primo.UI по отдельности рабочие. Далее надо связать Primo.UI и Primo.WebApi, настроив реверс-прокси для API. 
Предварительно надо установить модули IIS из комплекта поставки (обязательно в приведенной ниже последовательности), обеспечивающие 
функциональность реверс-прокси:  
`rewrite_amd64_en-US.msi`  
`requestRouter_amd64.msi`  

На узле Primo.UI настраиваем реверс-прокси для API.

Иконка оснастки управления правилами URL Rewrite:

![](../../../orchestrator-new/resources/install/windows/iis-41-urlrewrite.PNG)

Добавление правила URL Rewrite:

![](../../../orchestrator-new/resources/install/windows/iis-42-urlrewrite-rules.PNG)

Выбор шаблона правила URL Rewrite:

![](../../../orchestrator-new/resources/install/windows/iis-43-urlrewrite-template.PNG)

Параметры правила URL Rewrite:

![](../../../orchestrator-new/resources/install/windows/iis-44-urlrewrite-params.PNG)

Параметры правила URL Rewrite:
* Name: Reverse Proxy to API
* Pattern: ^api/(.*)
* Rewrite URL: http://localhost:5001/api/{R:1} 

Правило URL Rewrite добавлено:

![](../../../orchestrator-new/resources/install/windows/iis-45-urlrewrite-added.PNG)

Чтобы ARR заработал, надо его активировать. Для этого попробуйте добавить «Reverse Proxy» правило:

![](../../../orchestrator-new/resources/install/windows/iis-46-reverseproxy.PNG)

IIS выдаст предупреждение об активации ARR, на которое надо согласиться и нажать «ОК»:

![](../../../orchestrator-new/resources/install/windows/iis-47-warning.PNG)

Добавлять «Reverse Proxy» правило не надо, это все нужно было только для активации ARR. Поэтому нажмите «Cancel»:

![](../../../orchestrator-new/resources/install/windows/iis-48-cancel.PNG)

Теперь ARR активировано, и узел Primo.UI может работать как реверс-прокси.

Управлять правилами также можно из Web.config (секция <rewrite/>) узла.

Расположение Web.config узла Primo.UI:

![](../../../orchestrator-new/resources/install/windows/iis-49-webconfig.PNG)

Секция <rewrite/> Web.config:

![](../../../orchestrator-new/resources/install/windows/iis-50-rewrite.PNG)

Для каждого узла – Primo.UI и Primo.WebApi настройте максимальный размер загружаемых файлов.

Размер файлов для узла Primo.UI:

![](../../../orchestrator-new/resources/install/windows/iis-51-filesize.PNG)

Размер файлов для узла Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-52-filesize-webapi.PNG)

Проверяем, что в appsettings.ProdWin.json для UseIISIntegration = true. 
Остальные настройки appsettings.ProdWin.json выставляем аналогично описанному в статье [Установка WebApi как службы под Windows 2016 Server](../../orchestrator-new/install/windows/webapi-windows.md). 

:small_orange_diamond: **ВНИМАНИЕ!!! Файлы web.config для каждого узла идут в комплекте поставки: для Primo.WebApi в архиве WebApi-IIS.zip, для Primo.UI в папке Distr\Windows. 
Их содержимое может отличаться от приведенных в руководстве скриншотов.**

> Дополнительную информацию можно найти на официальном сайте Microsoft: [URL Rewrite Module Configuration Reference](https://learn.microsoft.com/en-us/iis/extensions/url-rewrite-module/url-rewrite-module-configuration-reference) и
[Using Failed Request Tracing to Trace Rewrite Rules](https://learn.microsoft.com/en-us/iis/extensions/url-rewrite-module/using-failed-request-tracing-to-trace-rewrite-rules).

Проверьте работоспособность, запуская приложение в браузере по адресу:

`https://[адрес]:44392`

Если WebApi работает с MS SQL SERVER, используя Windows-аутентификацию (Trusted_Connection=True), то для Application Pool с наименованием Primo.WebApi необходимо задать этого (доменного) Windows-пользователя. 

Правой кнопкой мыши откройте окно Advanced Settings и найдите свойство Identity:

![](../../../orchestrator-new/resources/install/windows/iis-53-advancedsettings.PNG)

Поменяйте значение свойства Identity – выберите Custom account и нажмите кнопку «Set…»:

![](../../../orchestrator-new/resources/install/windows/iis-54-customacc.PNG)

![](../../../orchestrator-new/resources/install/windows/iis-55-setcreds.PNG)

