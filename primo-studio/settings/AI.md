# Интеграция с AI

## YandexGPT

Для интеграции Primo с YandexGPT:
1.	[Создайте](https://passport.yandex.ru/registration) аккаунт в сервисе Яндекс ID, если его еще нет.
2.	Установите интерфейс командной строки Yandex Cloud (CLI) согласно официальной [документации](https://cloud.yandex.ru/ru/docs/cli/quickstart#install). 
3.	Получите OAuth-токен в Яндексе ID, перейдя по следующей [ссылке](https://oauth.yandex.ru/authorize?response_type=token&client_id=1a6990aa636648e9b2ef855fa7bec2fb). Если приложение запрашивает доступ к данным, разрешите. Это нужно для получения токена.
4.	Скопируйте токен в буфер обмена или сохраните его.
5.	Выполните действия из раздела [Создание профиля](https://cloud.yandex.ru/docs/cli/quickstart?#initialize). Результат должен иметь вид:
    ```
    token: y0_AgA...wvs7N4
    cloud-id: b1g159pa15cd********
    folder-id: b1g8o9jbt58********
    compute-default-zone: ru-central1-b
    ```

6.	Получите токен для работы с GPT, выполнив команду:
    ```
    yc iam create-token 
    ```
7.	[Перейдите](https://console.cloud.yandex.ru/cloud) в консоль управления Яндекс Cloud. 
8.	Обязательно скопируйте идентификатор папки - он понадобится для работы с GPT. 

    ![](<../../.gitbook/assets1/get-token-yandex-1.png>)
    
9.	Слева, в дереве навигации, перейдите на уровень организации и затем – в раздел «Права доступа». 

    ![](<../../.gitbook/assets1/get-token-yandex-2.png>)

10.	Выберите функцию **Изменить роли** у нужного пользователя.
 
    ![](<../../.gitbook/assets1/get-token-yandex-3.png>)

11.	Нажмите кнопку **Добавить роль**.
 
    ![](<../../.gitbook/assets1/get-token-yandex-4.png>)

12.	Выберите `ai.languageModels.user`.
 
    ![](<../../.gitbook/assets1/get-token-yandex-5.png>)

13.	Нажмите **Сохранить**.
14.	Перейдите в каталог `default` (либо нужный) и нажмите **YandexGPT**.
 
    ![](<../../.gitbook/assets1/get-token-yandex-6.png>)

15.	Заполните форму и отправьте заявку. Доступ должен появиться через несколько дней.
16.	Используйте токен (см. шаг 6) и ID папки (см. шаг 8) в следующих случаях:
    * в элементах YandexGPT из библиотеки **Primo.AI**;
    * для настройки интеграции Студии с YandexGPT при установленном плагине `Primo.AI.Plugin.dll`.

## GigaChat

Для интеграции Primo RPA с GigaChat:
1.	[Авторизуйтесь](https://developers.sber.ru/studio/workspaces/my-space/get/gigachat-api) на портале для разработчиков по Сбер ID. Если у вас нет Сбер ID, создайте его на странице авторизации.  В качестве Сбер ID используется ваш номер телефона. 
2.	Создайте проект GigaChat, если система не создала его сама. По умолчанию это проект с названием **My GigaChat**.
3.	Перейдите в проект GigaChat и нажмите **Сгенерировать ClientSecret** внизу страницы.
4.	Запомните ClientSecret и используйте его в элементе **Создать токен** из библиотеки **Primo.AI**. 

    Либо при настройке интеграции Студии с AI (плагин `Primo.AI.Plugin.dll`).

