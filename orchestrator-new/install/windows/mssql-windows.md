# Установка MS SQL SERVER 2019 и MS SQL Management Studio под Windows 2016 Server

1. В соответствии с имеющейся у компании лицензией, установите MSSQL SERVER, MS SQL MS, а также PowerShell.

2. Включите учетную запись суперпользователя **sa** базы данных. Для этого запустите **MS SQL Management Studio**. 

![](../../resources/install/windows/mssql-ms.PNG)

3. В разделе **Security** переключите Аутентификацию сервера как показано на скриншоте:

![](../../resources/install/windows/mssql-ms-auth.PNG)

4. Не перезагружаясь, в свойствах суперпользователя **sa** вводим пароль два раза:

![](../../resources/install/windows/mssql-ms-password.PNG)

5. В этом же окне в разделе **Status** включить Login. Перезагрузить сервер:

![](../../resources/install/windows/mssql-ms-status.PNG)

6. При подключении к базе данных в MS SQL Management Studio, выберите Аутентификацию, ввести логин и пароль, как показано на скриншоте:

![](../../resources/install/windows/mssql-ms-loginpw.PNG)

7. Разрешаем удаленное подключение к серверу БД:

![](../../resources/install/windows/mssql-ms-remconnect.PNG)

8. При помощи утилиты `C:\Windows\System32\SQLServerManager15.msc` включаем TCP/IP для сервера БД:

> Название и расположение утилиты зависит от версии и установки MS SQL SERVER

![](../../resources/install/windows/mssql-ms-tcpip.PNG)

9. Перезапускаем службу:

![](../../resources/install/windows/mssql-restart.PNG)