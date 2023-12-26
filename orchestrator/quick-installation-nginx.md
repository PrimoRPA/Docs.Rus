# Установка Оркестратора на веб-сервер Nginx 

Выбранная конфигурация:
* Windows Server 2019
* Nginx
* PostgreSQL
* RabbitMQ

## Видеоинструкция

С видеоинструкцией по установке Оркестратора можно ознакомиться [здесь](https://www.youtube.com/watch?v=mOTH1PWxSCs).

<a href="https://www.youtube.com/watch?v=mOTH1PWxSCs"><img src="https://raw.githubusercontent.com/PrimoRPA/Docs.Rus/main/.gitbook/assets1/quick-install-nginx.gif" width="850" title="hover text"></a>


[![Watch the video](<../.gitbook/assets1/quick-install-nginx.gif>)](https://www.youtube.com/watch?v=mOTH1PWxSCs)


## Начальная подготовка 
> *Подробнее в «Руководстве по предварительной настройке машины Оркестратора под Windows 2016 Server.docx»*.

1. Переименуем сервер, чтобы он имел простое и понятное название. Например, ORCHESTRATOR.
2. Раскомментируем в файле `C:\Windows\System32\drivers\etc\hosts` следующую строку:

![](<../.gitbook/assets1/orch-install-nginxserver-1.png>)

3. Разрешаем удаленные подключения к хосту. Заходим в **Start Menu > Control Panel > System > Advanced System Settings > Remote** и включаем настройку, как на рисунке ниже:

![](<../.gitbook/assets1/orch-install-nginxserver-2.png>)


## Шаг 1. Подготовка и установка дистрибутивов


## Шаг 2. Настройка PostgreSQL 
> *Подробнее в «Руководстве по предварительной настройке машины Оркестратора под Windows 2016 Server.docx».*

1. Создаем папку **distrib** на рабочем столе.
2. Создаем папку **Primo** в корне диска `C:\`.
3. Копируем в папку нужные дистрибутивы:

![](<../.gitbook/assets1/orch-install-nginxserver-3.png>)

4. Устанавливаем Google Chrome. Обновляем его до последней версии и делаем браузером по умолчанию.
5. Устанавливаем Notepad++. Все опции оставляем по умолчанию.
6. Устанавливаем PowerShell. При установке включаем все чекбоксы.

![](<../.gitbook/assets1/orch-install-nginxserver-4.png>)

7. Устанавливаем PostgreSQL Server (Руководство по установке PostgreSQL 13 под Windows 2016 Server) (подробнее в «Руководстве по установке PostgreSQL под Windows 2016 Server.docx»)

   7.1.	Распаковываем архив `postgresql-13.4-1-windows.zip` в папку `C:\Install`.\
   7.2.	Кликаем по файлу `C:\Install\postgresql-13.4-1-windows-x64.exe`.\
   7.3.	Выбираем **Да** в появившемся окне:

![](<../.gitbook/assets1/orch-install-nginxserver-5.png>)

   7.4.	В следующем окне выбираем **Далее**.

![](<../.gitbook/assets1/orch-install-nginxserver-6.png>)

   7.5.	Выбираем директорию (1), куда будет установлена программа. Оставляем все без изменения и жмем **Далее** (2).

![](<../.gitbook/assets1/orch-install-nginxserver-7.png>)

   7.6.	В окне выбора компонентов тоже все оставляем по умолчанию и нажимаем **Далее**.

![](<../.gitbook/assets1/orch-install-nginxserver-8.png>)

   7.7.	Прописываем путь `C:\Primo\PostgreSQL\Data` (1), где будут располагаться файлы базы данных Оркестратора и конфигурационные файлы, нажимаем **Далее** (2).

![](<../.gitbook/assets1/orch-install-nginxserver-9.png>)

   7.8.	В следующем окне вводим пароль\* (1) и его подтверждение (2) для суперпользователя БД (postgres), нажимаем **Далее**.

   > \**В дальнейшем пароль можно будет изменить в PostgreSQL.*

![](<../.gitbook/assets1/orch-install-nginxserver-10.png>)

   7.9.	В следующем окне не меняем настройки порта по умолчанию (5432) и нажимаем **Далее**.

![](<../.gitbook/assets1/orch-install-nginxserver-11.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-12.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-13.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-14.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-15.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-16.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-17.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-18.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-19.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-20.png>)

20-30

![](<../.gitbook/assets1/orch-install-nginxserver-21.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-22.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-23.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-24.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-25.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-26.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-27.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-28.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-29.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-30.png>)

30-40

![](<../.gitbook/assets1/orch-install-nginxserver-31.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-32.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-33.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-34.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-35.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-36.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-37.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-38.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-39-1.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-39-2.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-40.png>)

40-50

![](<../.gitbook/assets1/orch-install-nginxserver-41.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-42.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-43.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-44.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-45.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-46.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-47.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-48.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-49.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-50.png>)

50-60

![](<../.gitbook/assets1/orch-install-nginxserver-51.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-52.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-53.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-54.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-55.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-56.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-57.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-58.png>)

![](<../.gitbook/assets1/orch-install-nginxserver-59.png>)
