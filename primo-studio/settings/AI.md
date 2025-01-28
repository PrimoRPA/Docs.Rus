# Интеграция с AI

## Интеграция с YandexGPT

Для интеграции Primo RPA с YandexGPT:

1.	[Создайте](https://passport.yandex.ru/registration) аккаунт в сервисе Яндекс ID, если у вас его нет.

2. **Установите Yandex Cloud CLI**:  
   - Скачайте и установите **Yandex Cloud CLI**, следуя [официальной инструкции](https://cloud.yandex.ru/ru/docs/cli/quickstart#install).  
   - После установки выполните команду `yc init`, чтобы привязать **CLI** к вашему аккаунту.

3. **Получите OAuth-токен**:  
   - Перейдите по [этой ссылке](https://oauth.yandex.ru/authorize?response_type=token&client_id=1a6990aa636648e9b2ef855fa7bec2fb).  
   - Разрешите доступ, если это потребуется.  
   - Скопируйте OAuth-токен и сохраните его. Он понадобится для дальнейших шагов.

4.	Выполните действия из раздела [Создание профиля](https://cloud.yandex.ru/docs/cli/quickstart?#initialize). Выполните команды для создания профиля:

```
   yc config set token <OAuth-токен>
   yc config set cloud-id <Cloud-ID>
   yc config set folder-id <Folder-ID>
   yc config set compute-default-zone ru-central1-b
```   


Получите результат, который должен иметь вид:

```
    token: y0_AgA...wvs7N4
    cloud-id: b1g159pa15cd********
    folder-id: b1g8o9jbt58********
    compute-default-zone: ru-central1-b
```

5.	Получите IAM-токен для работы с GPT, выполнив команду:
    ```
    yc iam create-token 
    ```

   > **Примечание:** Время жизни IAM-токена не превышает 12-ти часов, но рекомендуется запрашивать его каждый час.

6.	**Перейдите в консоль управления Yandex Cloud**:  
   - Откройте [консоль Yandex Cloud](https://console.cloud.yandex.ru/cloud).  
   - Скопируйте *идентификатор папки (Folder ID)*. Он потребуется для работы с GPT.



        ![](<../../.gitbook/assets1/get-token-yandex-1.png>)
    

7.	Слева, в дереве навигации, выберите уровень организации и затем –  раздел «Права доступа». 

    ![](<../../.gitbook/assets1/get-token-yandex-2.png>)


   - Найдите нужного пользователя и выберите функцию *Изменить роли*.  
   - Нажмите кнопку *Добавить роль*.  
   - В выпадающем списке выберите `ai.languageModels.user`.  
   - Нажмите *Сохранить*.

    
 
        ![](<../../.gitbook/assets1/get-token-yandex-3.png>)


 
        ![](<../../.gitbook/assets1/get-token-yandex-4.png>)



        ![](<../../.gitbook/assets1/get-token-yandex-5.png>)


8. **Создайте платежный аккаунт**:  
   - В консоли Yandex Cloud перейдите в каталог `default` или нужный вам каталог.  
   - Нажмите на **YandexGPT** и заполните форму создания платежного аккаунта.
 
    ![](<../../.gitbook/assets1/get-token-yandex-6.png>)

9.	Используйте IAM-токен и ID папки для интеграции:
    * В элементах [YandexGPT](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt) из библиотеки [**Primo.AI**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai);
    * В настройках интеграции Студии с YandexGPT после [установки плагина `Primo.AI.Plugin.dll`](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/settings#ai).

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
   \
   \
   **Способ 1**
   
   * Скачайте библиотеку [**Primo.AI**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai) через менеджер зависимостей Студии.
   * В элементе **GigaChat > [Получить токен](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_gettoken)** укажите ваши авторизационные данные. В ответе робот вернет токен.
   * После получения токена можно отправлять вопросы в чат через элемент **GigaChat > [Вопрос в чат](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_chatmessage)**. 
  
    **Способ 2**
   \
   \
   Если токен нужен для настройки интеграции Студии со Sber AI, его также можно [получить через Postman](https://developers.sber.ru/docs/ru/gigachat/api/authorization#shag-2-poluchenie-tokena-dostupa-v-obmen-na-avtorizatsionnye-dannye). Для этого вам понадобятся авторизационные данные, которые вы сохранили в шаге 4.

   Полученный токен укажите в разделе **Файл > Настройки > Интеграция > AI** в полях **Token** и **Key** для языковой модели Sber AI. Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#ai).

