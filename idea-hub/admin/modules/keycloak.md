# Интеграция с Keycloak

Возможность интеграции с Keycloak появилась в версии Idea Hub 25.3. В этом разделе приведена инструкция по настройке Keycloak.

## Установка модулей 

Сначала потребуется установить в Idea Hub модули Keycloak и OpenID Connect. 

Их можно установить командой:
```
drush in keycloak -y
```

Либо установить через веб-интерфейс Idea Hub:
1. Войдите в Idea Hub с правами администратора.
1. В административном меню выберите пункт **Расширения**.
1. С помощью строки **Фильтр** найдите модули Keycloak, OpenID Connect и проставьте напротив них галочки.
1. Нажмите **Установить** и дождитесь, когда появится уведомление об успешном статусе установки модулей.



## Добавить keycloak клиент в Ideahub:
- Перейдите на страницу /admin/config/people/openid-connect/add/keycloak

- Занесите в поле **Имя** значение _**keycloak**_. Это важно! Текущая версия модуля смотрит конфигурацию конкретного клиента, поэтому нам доступно только название _**keycloak**_
![keycloak.png](/.attachments/keycloak-55b851b8-2a19-43f4-807f-56b0633cf812.png)

- Указываем название клиента (Client ID). У нашего тестового сервера это **_ideahub_**
![keycloak_ideahub.png](/.attachments/keycloak_ideahub-029dabe5-a556-47ad-815e-9c4e67971a3a.png)

- Следующее поле **Client secret**. У клиента на вкладке credentials это поле есть, его значение выглядит  примерно так: **InBPPiGdzYfP9oYrVL3qwTv5BdY1ELtl**

- Далее нужно указать базовый урл keycloak (Keycloak base URL), например наш тестовый keycloak это https://10.0.0.159:8443/

- Далее нужно указать Keycloak realm, его можно найти в keycloak в самом верху справа (у нас это test)
![realm.png](/.attachments/realm-ce1f2021-c579-4e60-b712-dd856fdb4159.png)

- Дальше я бы посоветовал включить следующие опции "**Update email address in user profile**", "**Enable user role mapping**". Последняя опция позволяет при создании пользователя при логине обновлять его роли.
Например тут я указал что для пользователей keycloak с ролью **role-ideahub** нужно добавлять роль **Бизнес-Пользователь**/
![role.png](/.attachments/role-ccd3c5ca-9954-4b58-ab04-970399d3589d.png)

- После того как всё настроено необходимо нажать кнопку "Сохранить" внизу страницы, а так же сохранить для следующей настройки значение поля Redirect URL

- Дальше надо перейти на страницу настройки OpenID **/admin/config/people/openid-connect/settings**

- И включить следующие настройки:  "**Save user claims on every login**", "**Override registration settings**"

- Предпоследним шагом будет настройки полей "**User claims mapping**". Сейчас можно настроить поля: Изображение, Часовой пояс, Почту, Имя, Телефон.

- Не забыть нажать кнопку "Сохранить конфигурацию" внизу страницы.

## Настроить сам keycloak:

- На странице редактирования клиента keycloak (в **Ideahub**) ```/admin/config/people/openid-connect/keycloak/edit``` будет url:

![url.png](/.attachments/url-3dcbb4a5-4300-4683-adde-c2ecc892fbf8.png)

- Url сверху который нужно добавить к валидным урлам клиента keycloak (в keycloak):
Заходим в нашего клиента
![keycloak_ideahub.png](/.attachments/keycloak_ideahub-029dabe5-a556-47ad-815e-9c4e67971a3a.png)
А уже внутри клиента добавляем урл
![url_saved.png](/.attachments/url_saved-88b9a380-692f-454f-ba7a-595cd9401933.png)

