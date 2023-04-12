# Установка IIS

Данная инструкция является частью руководства [по установке WebApi и UI на IIS под Windows 2016 Server](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/install-webapi-introduction.md) и выполняется после включения компьютера в AD (не нужно, если используется DHCP).

**Как установить IIS**:

1\. Входим в систему с локальной учетной записью **Administrator**:

![](<../../../../.gitbook/assets/install-webapi-iis-1.png>)

2\. В **Server Manager** (откроется автоматически после входа в систему, или запустить из главного меню), выбираем **Add Roles and Features**:

![](<../../../../.gitbook/assets/install-webapi-iis-2.png>)

3\. В **Before you begin** нажимаем кнопку **Next**:

![](<../../../../.gitbook/assets/install-webapi-iis-3.png>)

4\. В **Installation Type** оставляем по умолчанию:

![](<../../../../.gitbook/assets/install-webapi-iis-4.png>)

5\. В **Server Selection** оставляем по умолчанию:

![](<../../../../.gitbook/assets/install-webapi-iis-5.png>)

6\. В **Server Roles** выбираем **Web Server (IIS)**: 

![](<../../../../.gitbook/assets/install-webapi-iis-6.png>)

7\. В **Features** оставляем по умолчанию:

![](<../../../../.gitbook/assets/install-webapi-iis-7.png>)

8\. В **Web Server Role (IIS)** нажимаем кнопку **Next**:

![](<../../../../.gitbook/assets/install-webapi-iis-8.png>)

9\. В **Role Services** выбираем **HTTP Redirection** и **Windows Authentication**:

![](<../../../../.gitbook/assets/install-webapi-iis-9.png>)

![](<../../../../.gitbook/assets/install-webapi-iis-10.png>)

10\. В **Confirmation** наживаем кнопку **Install** и дожидаемся завершения установки:

![](<../../../../.gitbook/assets/install-webapi-iis-11.png>)

:white_check_mark: **Готово**: веб-сервер IIS успешно установлен в Windows 2016 Server. Для завершения установки WebApi и UI на IIS **перейдите к [разворачиванию узлов веб-приложения](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/web-app-nodes.md)**.
