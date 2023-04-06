# Установка MS SQL Server 2019 и MS SQL Management Studio

Раздел содержит инструкцию по установке MS SQL Server 2019 и MS SQL Management Studio под Windows 2016 Server. 

**Для установки выполните шаги:**

1. Запустите установку MSSQL SERVER из `C:\Install\MSSQL.zip\SQL2019-SSEI-Dev.exe`.
1. Установите MS SQL MS из `C:\Install\MSSQL.zip\SSMS-Setup-RUS.exe`.
1. Установите PowerShell из `C:\Install\PowerShell-7.1.3-win-x64.msi`.
1. Включите учетную запись суперпользователя **sa** базы данных. Для этого запустите MS SQL Management Studio:

![](<../../../.gitbook/assets/install-mssql-start.png)

5. В разделе Security переключите Аутентификацию сервера, как показано на рисунке ниже:

![](<../../../.gitbook/assets/install-mssql-2.png>)

6. Не перезагружаясь, в свойствах суперпользователя **sa** введите пароль 2 раза:

![](<../../../.gitbook/assets/install-mssql-3.png>)

7. В этом же окне в разделе Status включите Login. Перезагрузите сервер:

![](<../../../.gitbook/assets/install-mssql-4.png>)

8.	При подключении к базе данных в MS SQL Management Studio, выберите Аутентификацию, введите логин и пароль, как показано на рисунке:

![](<../../../.gitbook/assets/install-mssql-5.png>)

9. Последовательно выполнить команды  из C:\Install\MSSQL.zip\get_cpu_hdd_host.txt:

![](<../../../.gitbook/assets/install-mssql-6.png>)

![](<../../../.gitbook/assets/install-mssql-7.png>)

![](<../../../.gitbook/assets/install-mssql-8.png>)

![](<../../../.gitbook/assets/install-mssql-9.png>)

![](<../../../.gitbook/assets/install-mssql-10.png>)

![](<../../../.gitbook/assets/install-mssql-11.png>)

![](<../../../.gitbook/assets/install-mssql-12.png>)

**При создании процедуры get_cpu_hdd_host нужно следить, чтобы случайно не внести изменения в текст скрипта. Недопустимо вносить даже не значимые с точки зрения кода скрипта пробелы, пустые строки, менять регистр!**

10.	Разрешите удаленное подключение к серверу БД:

![](<../../../.gitbook/assets/install-mssql-13.png>)

11. При помощи утилиты C:\Windows\System32\SQLServerManager15.msc включите TCP/IP для сервера БД:

![](<../../../.gitbook/assets/install-mssql-14.png>)

12. Перезапустите службу:

![](<../../../.gitbook/assets/install-mssql-15.png>)
