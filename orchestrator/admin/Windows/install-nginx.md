# Установка Nginx в качестве службы 
Раздел содержит инструкцию по установке Nginx в качестве службы под Windows 2016 Server.

**Для установки Nginx выполните шаги:**

1\. Разархивируйте файл nginx-service.zip, который идет в комплекте поставки, в директорию `C:\Primo\nginx-1.21.1` (версия nginx может изменится):

![](<../../../.gitbook/assets/install-mssql-start.png>)

2\.	Щелкнуте правой кнопкой мыши по пустому простанству и откройте PowerShell от имени Администратора:

![](<../../../.gitbook/assets/install-mssql-start.png>)

3\. Выполните команду:
```
.\nginx-service.exe install
```
![](<../../../.gitbook/assets/install-mssql-start.png>)

4\. После успешной установки службы можно запускать/останавливать ее в разделе **Управление сервером > Службы**:

![](<../../../.gitbook/assets/install-mssql-start.png>)

Альтернативный способ - с использованием окна PowerShell*. Для остановки и запуска используйте команды:
```
> net stop nginx
> net start nginx
```

![](<../../../.gitbook/assets/install-mssql-start.png>)

*\*После установки службы Nginx PowerShell необходимо перезапустить*.
