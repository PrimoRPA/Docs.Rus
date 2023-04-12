# Разворачивание узлов веб-приложения

Данная инструкция является частью руководства [по установке WebApi и UI на IIS под Windows 2016 Server](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/install-webapi-introduction.md) и выполняется после шагов:
* [включение компьютера в AD](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/install-webapi-introduction.md#%D0%B2%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D0%BC%D0%BF%D1%8C%D1%8E%D1%82%D0%B5%D1%80%D0%B0-%D0%B2-ad) - не нужно, если используется DHCP;
* [установка IIS](https://github.com/PrimoRPA/Docs.Rus/edit/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/webapi-install-iis.md).

## Как развернуть узлы веб-приложения

1\. Открываем оснастку для управления IIS:

![](<../../../../.gitbook/assets/install-webapi-node-1.png>)

2\. Создаем системную переменную окружения ASPNETCORE_ENVIRONMENT= ProdWin. Для этого в PoweShell выполняем команду:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

3\. Для узла WebApi создаем отдельный неуправляемый Application Pool с наименованием **Primo.WebApi** (рисунки 28 – 30), Start Mode = AlwaysRunning и Regular Time Interval (minutes) = 0:

![](<../../../../.gitbook/assets/install-webapi-node-2.png>)

![](<../../../../.gitbook/assets/install-webapi-node-3.png>)

![](<../../../../.gitbook/assets/install-webapi-node-4.png>)

4\. Создаем папки C:\Primo\UI и C:\Primo\WebApi, в которые разархивируем UI.zip и 
WebApi-IIS.zip из комплекта поставки (рисунки 31, 32):

![](<../../../../.gitbook/assets/install-webapi-node-5.png>)

![](<../../../../.gitbook/assets/install-webapi-node-6.png>)

5\. Добавляем веб-узел Primo.WebApi (рисунки 33 – 35), устанавливаем для него ранее созданный Application Pool с наименованием Primo.WebApi:

![](<../../../../.gitbook/assets/install-webapi-node-7.png>)

![](<../../../../.gitbook/assets/install-webapi-node-8.png>)

![](<../../../../.gitbook/assets/install-webapi-node-9.png>)

6\. Чтобы Primo.WebApi заработал под IIS, устанавливаем из комплекта поставки:
* aspnetcore-runtime-3.1.15-win-x64.exe\
  (https://download.visualstudio.microsoft.com/download/pr/ae6e6b5b-5e7c-45f9-a668-cb1899f22e46/9c917acfab934ddd64340ba46490264e/aspnetcore-runtime-3.1.15-win-x64.exe);
* dotnet-hosting-3.1.15-win.exe\
  (https://download.visualstudio.microsoft.com/download/pr/c8eabe25-bb2b-4089-992e-48198ff72ad8/a55a5313bfb65ac9bd2e5069dd4de5bc/dotnet-hosting-3.1.15-win.exe).
  
И перезагружаем компьютер.

7\. Для создания узла UI сначала создадим для веб-сервера SSL-сертификат* , так как этот узел будет работать по https (рисунки 36 – 39):

*\***Для промышленного узла необходимо использовать SSL-сертификат, выданный доверенным удостоверяющим центром.***

![](<../../../../.gitbook/assets/install-webapi-node-10.png>)

![](<../../../../.gitbook/assets/install-webapi-node-11.png>)

![](<../../../../.gitbook/assets/install-webapi-node-12.png>)

![](<../../../../.gitbook/assets/install-webapi-node-13.png>)

8\. Добавляем веб-узел Primo.UI (рисунок 40), устанавливаем для него Application Pool с наименованием DefaultAppPool и выбираем ранее созданный SSL-сертификат с наименованием Primo: 

![](<../../../../.gitbook/assets/install-webapi-node-14.png>)

На этом шаге узлы Primo.WebApi и Primo.UI по отдельности рабочие. Далее надо связать Primo.UI и Primo.WebApi, настроив реверс-прокси для API. Предварительно надо установить модули IIS из комплекта поставки (обязательно в приведенной ниже последовательности), обеспечивающие функциональность реверс-прокси:
* rewrite_amd64_en-US.msi
* requestRouter_amd64.msi
	На узле Primo.UI настраиваем реверс-прокси для API (рисунки 41 – 45):


![](<../../../../.gitbook/assets/install-webapi-node-15.png>)

![](<../../../../.gitbook/assets/install-webapi-node-16.png>)

![](<../../../../.gitbook/assets/install-webapi-node-17.png>)

![](<../../../../.gitbook/assets/install-webapi-node-18.png>)

![](<../../../../.gitbook/assets/install-webapi-node-19.png>)

![](<../../../../.gitbook/assets/install-webapi-node-20.png>)

![](<../../../../.gitbook/assets/install-webapi-node-21.png>)

![](<../../../../.gitbook/assets/install-webapi-node-22.png>)

![](<../../../../.gitbook/assets/install-webapi-node-23.png>)

![](<../../../../.gitbook/assets/install-webapi-node-24.png>)

![](<../../../../.gitbook/assets/install-webapi-node-25.png>)

![](<../../../../.gitbook/assets/install-webapi-node-26.png>)

![](<../../../../.gitbook/assets/install-webapi-node-27.png>)

![](<../../../../.gitbook/assets/install-webapi-node-28.png>)

![](<../../../../.gitbook/assets/install-webapi-node-29.png>)

![](<../../../../.gitbook/assets/install-webapi-node-30.png>)

:white_check_mark: **Готово**:
