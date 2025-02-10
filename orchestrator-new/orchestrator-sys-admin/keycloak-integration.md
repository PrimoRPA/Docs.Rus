# Интеграция с KeyCloak

В данном руководстве предполагается, что KeyCloak-сервер уже развернут и настроен.

Во флаговый энум типов авторизации (параметр `Auth:Type` конфигурационного файла WebApi) добавились значения KeyCloak1\* = 8 и KeyCloak2\*\* = 16. 
При наличии этого флага на форме авторизации отобразится кнопка **Войти с учетной записью KeyCloak**. Использовать одновременно оба флага не рекомендуется.	
Сначала потребуется создать *Realm* – для этого нужно войти в **Administration Console** на главной странице KeyCloak (рисунок 1) с правами администратора (рисунок 2):

> *\* - Сокращенный флоу*  
> *\*\* - Полный флоу с PKCE*

Рисунок 1 – Главная страница KeyCloak

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-1.PNG)

Рисунок 2 – Форма авторизации в **Administration Console**

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-2.PNG)

Нажимаем кнопку **Create Realm** и вводим параметры нового Realm:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-3.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-4.PNG)

После создания нового Realm система автоматически переключит на него:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-5.PNG)

Этот параметр будет использоваться при настройке конфигурационного файла службы WebApi:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-6.PNG)

Далее создаем Client – переходим на форму **Clients** со списком клиентов и нажимаем кнопку **Create Client**:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-7.PNG)

В мастере создания Client на первом шаге задаем ClientID, Name и Description:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-8.PNG)

Параметр ClientID будет использоваться при настройке конфигурационного файла службы WebApi:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-9.PNG)

В мастере создания Client на втором шаге включается **Client authentication** и **Authorization**, остальные по умолчанию:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-10.PNG)

На вкладке **Credentials** у созданного Client нужно скопировать значение параметра *Client secret*, 
зашифровать его утилитой шифрования паролей, и добавить в конфигурационный файл службы WebApi:

Копирование *Client secret*

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-11.PNG)

Шифрование *Client secret* утилитой Primo.Orchestrator.PasswordEncryptor

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-12.PNG)

*ClientSecret* в конфигурационном файле службы WebApi

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-13.PNG)

Для типа авторизации KeyCloak2 = 16 нужно в конфигурационном файле WebApi настроить (только IP и порт) `RedirectUrl`, и скопировать его в **Valid redirect URLs** для Client:

Настройка `RedirectUrl` в конфигурационном файле службы WebApi

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-14.PNG)

**Valid redirect URLs** для Client

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-15.PNG)

Встроенной учетной записи, ассоциированной с Client –  service-account-orch – надо добавить роль для разрешения управления Realm. 
Открыть вкладку **Users**, выбрать пользователя service-account-orch, открыть вкладку **Role mapping** и установить фильтр *Filter by clients* и выбрать роль «manage-realm»:

Вкладка **Users**

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-16.PNG)

Вкладка **Role mapping**

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-17.PNG)

Выбор роли «manage-realm»

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-18.PNG)

Далее нужно настроить роли пользователей, которые будут использованы для сопоставления с ролями Оркестратора. Переходим на вкладку **Realm roles**:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-19.PNG)

Добавляем роли с префиксом «orch-», чтобы потом по нему производить поиск:

Добавление роли

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-20.PNG)

Список ролей, отфильтрованный по префиксу «orch-»

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-21.PNG)

Дальше создаем пользователей, которые будут авторизоваться в Оркестраторе. Переходим на вкладку **Users**:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-22.PNG)

Создаем пользователя Оркестратора, сразу включаем *Email verified*:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-23.PNG)

Устанавливаем созданному пользователю пароль. Переходим на вкладку **Credentials**:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-24.PNG)

Назначаем пароль, сразу отмечаем его постоянным – отключаем *Temporary*:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-25.PNG)

Ассоциируем пользователя с ранее созданными ролями для Оркестратора:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-26.PNG)

Чтобы авторизация работала, необходимо, чтобы эти роли средствами Оркестратора были связаны с ролями Оркестратора:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-27.PNG)

В конфигурационном файле службы WebApi прописываем URL-адрес:порт KeyCloak-сервера:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/Keycloak-28.PNG)

Если задан `СonfigurationUrl`, то `AuthUrl`, `TokenUrl` и `LogoutUrl` заполняются на основе ответа этого эндпоинта, и их можно оставить пустыми/удалить из конфигурационного файла службы WebApi.



