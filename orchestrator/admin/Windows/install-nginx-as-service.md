# Установка Nginx как службы 
Раздел содержит инструкцию по установке Nginx в качестве службы под Windows 2016 Server.

**Как установить Nginx:**

1\. Распакуйте архив `nginx-service.zip`, который идет в комплекте поставки, в директорию `C:\Primo\nginx-1.21.1` (версия nginx может изменится):

![](<../../../.gitbook/assets/install-nginx-1.png>)

2\.	Щелкните правой кнопкой мыши по пустому пространству и откройте PowerShell от имени Администратора:

![](<../../../.gitbook/assets/install-nginx-2step.png>)

3\. Выполните команду:
```
> .\nginx-service.exe install
```
![](<../../../.gitbook/assets/install-nginx-3.png>)

4\. Успешно установленную службу можно запускать/останавливать в разделе **Управление сервером > Службы**:

![](<../../../.gitbook/assets/install-nginx-4.png>)

Альтернативный способ - с использованием окна PowerShell*. Для остановки/запуска используйте команды:
```
> net stop nginx
> net start nginx
```

![](<../../../.gitbook/assets/install-nginx-5.png>)

*\*После установки службы Nginx PowerShell необходимо перезапустить*.

:white_check_mark: **Готово**: Nginx успешно установлена как служба.
