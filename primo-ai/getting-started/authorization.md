# Авторизация

В системе возможно авторизоваться двумя способами:
1. По логину и паролю пользователя Primo AI. Это базовый тип входа. 
2. По логину и паролю пользователя Active Directory. Для входа используется технология единого входа (SSO). Администратор системы должен выполнить предварительные настройки на стороне Primo AI, чтобы пользователю AD стал доступен вход в приложение Primo AI.


## Вход с учетной записью Primo AI

1. Для входа в веб-приложение Primo AI введите адрес стартовой страницы.
2. В форме авторизации укажите тенант пользователя.
3. Введите логин и пароль пользователя.
4. После чего нажмите **Войти**.

![](</primo-ai/images/authorization.png>)

Система предоставляет встроенную учетную запись администратора со следующими данными:
* логин — `admin`
* пароль — `Qwe123!@#`

:small_orange_diamond: ***Важно**. После входа не забудьте поменять пароль*.


## Вход с учетной записью AD

### Начальные условия
Администратору Primo AI сначала необходимо привязать группу AD пользователя к существующей роли в Primo AI — это определит права доступа AD-пользователя к объектам в Primo AI. Подробнее см. здесь. Только после выполнения указанных условий будет доступна успешная авторизация по доменной учетной записи.

### Вход в систему
Введите адрес стартовой страницы Primo AI. В форме авторизации выберите **Войти с доменной учетной записью**.

![](</primo-ai/images/authorization-2.png>)

Укажите логин и пароль учетной записи Active Directory. Аутентификация* пользователя AD осуществляется средствами AD.


> \**Идентификация пользователя. ↑*



