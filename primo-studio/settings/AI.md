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

6.	Получите IAM-токен для работы с GPT, выполнив команду:
    ```
    yc iam create-token 
    ```

    Время жизни IAM-токена не превышает 12-ти часов, но рекомендуется запрашивать его каждый час.

7.	[Перейдите](https://console.cloud.yandex.ru/cloud) в консоль управления Yandex Cloud. 
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

15.	Заполните форму создания платежного аккаунта.
16.	Используйте токен (см. шаг 6) и ID папки (см. шаг 8) в следующих случаях:
    * в элементах YandexGPT из библиотеки **Primo.AI**;
    * для настройки [интеграции](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#integraciya) Студии с YandexGPT после установки плагина `Primo.AI.Plugin.dll`.

## GigaChat

Для интеграции Primo RPA с GigaChat:
1.	[Авторизуйтесь](https://developers.sber.ru/studio/workspaces/my-space/get/gigachat-api) на портале для разработчиков по Сбер ID. Если у вас нет Сбер ID, создайте его на странице авторизации. В качестве Сбер ID используется ваш номер телефона. 
2.	Создайте проект GigaChat, если система не создала его сама. По умолчанию это проект с названием **Mой GigaChat**. 

    ![](<../../.gitbook/assets1/add-project-gigachat.png>)

3. Перейдите в проект GigaChat и нажмите кнопку **Сгенерировать ClientSecret**.
4. Скопируйте и сохраните авторизационные данные.

   ![](<../../.gitbook/assets1/auth-data-sber.png>)

6. Получите токен. 

   :small_blue_diamond: ***Токен действует в течение 30 минут с момента выпуска.***
  
   **Способ 1**
   
   * Скачайте библиотеку **Primo.AI** через менеджер зависимостей Студии.
   * В элементе **GigaChat > Создать токен** укажите ваши авторизационные данные. В ответе робот вернет токен.
   * После получения токена можно отправлять вопросы в чат через элемент **GigaChat > Вопрос в чат**. 
  
    **Способ 2**

   Если токен нужен для настройки [интеграции](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#integraciya) Студии со Sber AI, его также можно [получить через Postman](https://developers.sber.ru/docs/ru/gigachat/api/authorization#shag-2-poluchenie-tokena-dostupa-v-obmen-na-avtorizatsionnye-dannye). Для этого вам понадобятся авторизационные данные, которые вы сохранили в шаге 4.

   Полученный токен укажите в разделе **Файл > Настройки > Интеграция > AI** в полях **Token** и **Key** для языковой модели Sber AI. 

