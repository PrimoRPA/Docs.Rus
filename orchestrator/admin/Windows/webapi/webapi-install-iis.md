# Установка IIS

1\.Входим в систему с локальной учетной записью Administrator:

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

:white_check_mark: **Готово**: веб-сервер IIS успешно установлен. Можно переходить к разворачиванию узлов веб-приложения.
