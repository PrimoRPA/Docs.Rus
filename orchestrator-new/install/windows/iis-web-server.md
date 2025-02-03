# Установка Оркестратора на веб-сервер IIS

Конфигурация:
-	Windows Server 2019
-	Internet Information Services (IIS)
-	PostgreSQL
-	RabbitMQ

## Видеоинструкция

С видеоинструкцией по установке Оркестратора на веб-сервер IIS можно ознакомиться [здесь](https://www.youtube.com/watch?v=IAIRmChw65k&ab_channel=PrimoRPA).

<a href="https://www.youtube.com/watch?v=IAIRmChw65k"><img src="https://raw.githubusercontent.com/PrimoRPA/Docs.Rus/main/.gitbook/assets/video_preview/test_gif.gif" width="850" title="hover text"></a>


## Начальная подготовка 
> *Подробнее в «Руководстве по предварительной настройке машины Оркестратора под Windows 2016 Server.docx».*

1.	Переименовываем сервер для простоты и удобства. Например, назовем его **ORCHESTRATOR**.
2.	Создаем папку для размещения дистрибутивов `Primo.Distrib`.
3.	Скачиваем и распаковываем архив с дистрибутивом Оркестратора в ранее созданную папку `Primo.Distrib`.

## Шаг 1. Включаем IIS 
> *Подробнее в «Руководство по установке WebApi и UI на IIS под Windows 2016 Server.docx» с 7-ой страницы и далее.*

1. Заходим в **Диспетчер > Управление > Добавить роли и компоненты**.

![](../resources/quick-installation/1-iis.png)

2. Нажимаем везде **Далее** (все оставляем по умолчанию).
3. На странице **Роли сервера** устанавливаем чек-бокс **Веб-сервер (IIS)**.
4. На странице **Службы ролей** устанавливаем чек-бокс **Проверка подлинности Windows** и **Перенаправление HTTP**.
5. После установки запускаем IIS.

![](../resources/quick-installation/2-iis.png)

6. Заходим в **Пулы приложений** и добавляем новый пул:

![](../resources/quick-installation/3-iis.png)

7. Назначаем владельцем пула Администратора (локальная УЗ Windows). 

![](../resources/quick-installation/4-iis.png)

![](../resources/quick-installation/5-iis.png)

![](../resources/quick-installation/5-2-iis.png)


## Шаг 2. Копируем и распаковываем архивы

Создаем папку `C:\Primo`, после чего:
1.	Копируем в нее архивы: `UI.zip`, `MachineInfo.zip`, `RDP2.zip`, `States.zip`, `WebApi-IIS.zip`, `Notifications.zip`, `RobotLogs.zip`.
2.	Переименовываем `WebApi-IIS.zip` в `WebApi.zip`.
3.	Распаковываем каждый архив в эту же директорию.
4.	Удаляем все архивы  - они нам далее не понадобятся.

## Шаг 3. Установка модулей и приложений
Ставим по порядку:
1.	`aspnetcore-runtime-3.1.15-win-x64.exe`.
2.	`ChromeStandaloneSetup64.exe` (устанавливаем и обновляем до последней версии).
3.	`dotnet-hosting-3.1.15-win.exe`.
4.	`PowerShell-7.1.3-win-x64.msi`.
5.	`requestRouter_amd64.msi`.
6.	`rewrite_amd64_en-US.msi`.
7.	`postgresql-13.4-1-windows.zip` (ставим согласно инструкции «Руководство по установке PostgreSQL под Windows 2016 Server.docx»).
8.	`dbeaver-ce-23.1.4-x86_64-setup.exe` (скачиваем с официального сайта).
9.	`npp.8.5.5.Installer.x64.exe`.

## Шаг 4. Настройка IIS

1. Добавляем сайт для WebApi. Для этого выбираем пункт контекстного меню узла **Сайты > Добавить веб-сайт**.

![](../resources/quick-installation/6-iis.png)

![](../resources/quick-installation/6-2-iis.png)

2. Добавляем самоподписанный сертификат. Выбираем **IIS > Сертификаты сервера > Создать самозаверенный сертификат**.

![](../resources/quick-installation/7-iis.png)

![](../resources/quick-installation/8-iis.png)

3. Добавляем сайт для UI и назначаем ему этот сертификат.

![](../resources/quick-installation/9-iis.png)

![](../resources/quick-installation/10-iis.png)

4. Перезагружаем сервер.
5. Запускаем IIS.
6. Выбираем сайт **Primo.UI > Переопределение URL-адресов**.

![](../resources/quick-installation/11-iis.png)

7. Далее нажимаем **Добавить правило** - **Пустое правило**.

![](../resources/quick-installation/12-1-iis.png)

8. Заполняем:
* Имя: `Reverse Proxy to API`
* Шаблон: `^api/(.*)`
* URL-адрес переопределения: http://localhost:5001/api/{R:1}

![](../resources/quick-installation/12-2-iis.png)

9. Добавлять обратный прокси-сервер не нужно, сначала создаем правило через нажатие кнопки **Обратный прокси-сервер**.

![](../resources/quick-installation/13-iis.png)

10. В этом окне нажимаем еще раз **ОК**.

![](../resources/quick-installation/14-iis.png)

11. И в следующем окне нажимаем **Отмена**.

![](../resources/quick-installation/15-iis.png)

12. Заменяем файл `web.config` в папке `C:\Primo\UI`:
   * берем файл из комплекта поставки `…\Primo Orchestrator 1.23.7.0\Distr\Windows\web.config`;
   * копируем его и вставляем с заменой в папку `C:\Primo\UI`.

![](../resources/quick-installation/16-iis.png)

## Шаг 5. Настройка и запуск служб

:small_blue_diamond: *Перечисленные ниже руководства входят в комплект поставки Оркестратора.*

Все дальнейшие настройки будут выполняться в PowerShell согласно руководствам по установке служб. 

1. Настраиваем и запускаем службу MachineInfo. Используем для этого «Руководство по установке MachineInfo как службы под Windows 2016 Server.docx».
2. Настраиваем и запускаем службу Notifications. Используем для этого «Руководство по установке Notifications под Windows 2016 Server.docx».
3. Настраиваем и запускаем службу RDP2. Используем для этого «Руководство по установке RDP2 под Windows 2016 Server.docx».
4. Настраиваем и запускаем службу RobotLogs. Используем для этого «Руководство по установке RobotLogs как службы под Windows 2016 Server.docx».
5. Настраиваем и запускаем службу States. Используем для этого «Руководство по установке States под Windows 2016 Server.docx».

## Шаг 6. Установка RabbitMQ Server 

Для установки RabbitMQ воспользуемся инструкцией из комплекта поставки: «Руководство по установке RabbitMQ под Windows 2016 Server.docx».


## Шаг 7. Настраиваем службу WebApi 
> *Подробнее в «Руководстве по установке WebApi как службы под Windows 2016 Server.docx» на 1-ой странице*. 

Редактируем конфигурационный файл службы WebApi (C:\Primo\WebApi\appsettings.ProdWin.json).

Меняем строки в секции **ConnectionStrings**:
* значение HOST;
* значение USER ID;
* значение PASSWORD.

![](../resources/quick-installation/17-iis.png)

Исправляем секцию **RobotDeployment**:

![](../resources/quick-installation/18-iis.png)

Правим секцию **RDP**:

![](../resources/quick-installation/19-iis.png)

Создадим папки в корне диска `C: RpaProjects`, `C: OrchNuGet`.

Перезагружаем сервер.


## Шаг 8. Проверка работы Оркестратора

1. Проверяем состояние службы IIS, статусы пулов приложений и статусы работы сайтов:

![](../resources/quick-installation/20-iis.png)

![](../resources/quick-installation/21-iis.png)

2. Проверяем статус службы Primo в службах Windows:

![](../resources/quick-installation/22-iis.png)

3. Проверяем работу сервера Rabbit, переходим по ссылке: http://localhost:15672. 

   Логин: `admin`

   Пароль: `Qwe123!@#`

![](../resources/quick-installation/23-iis.png)

4. Проверяем работу Оркестратора, переходим по ссылке: https://localhost:44392/.

   Логин: `admin`

   Пароль: `Qwe123!@#`

:white_check_mark: **На этом установка и базовая настройка Оркестратора завершены.**




