# Решить ReCapcha v2

![](<../../../../.gitbook/assets1/linux_items-extra/recaptcha-v2.png>)

Элемент решает капчу формата reCAPTCHA v2. Это популярный вид капчи, также известный как "Я не робот" reCAPTCHA, и выглядит так:

![](<../../../../.gitbook/assets/image (604).png>)

Решить reCAPTCHA v2 с помощью нашего метода очень легко, это не требует эмуляции браузера:

1. Посмотрите исходный код элемента на странице, где вы встретили reCAPTCHA.

   ![](<../../../../.gitbook/assets/image (486).png>)

1. Найдите ссылку, которая начинается с _www.google.com/recaptcha/api2/anchor_ или найдите параметр _data-sitekey_.
1. Скопируйте значение параметра _k_ из ссылки или значение _data-sitekey_.

   ![](<../../../../.gitbook/assets/image (587).png>)

1. Найдите элемент с id _g-recaptcha-response_ и сделайте его видимым, удалив параметр _display:none_.

   ![](<../../../../.gitbook/assets/image (500).png>)

**Внимание:** иногда содержимое страницы генерируется динамически и вы можете не найти данный элемент.\
В таком случае вам нужно изучить скрипты, отвечающие за генерацию содержимого страницы. Опция "Inspect" в Google Chrome может помочь в этом.

1. На странице отобразится текстовое поле. Всё что вам остается сделать — вставить полученный токен в это поле и отправить форму.

   ![](<../../../../.gitbook/assets/image (475).png>)

1. Поздравляем, вы решили reCAPTCHA!


## Начальные условия

1. [Установите](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio-linux/projects/manage-dependencies#menedzher-zavisimostei) пакет Primo.2Captcha.Linux в Primo RPA Studio версии 1.24.8.2 и выше.
1. Зарегистрируйтесь на сайте https://2captcha.com, чтобы получить ключ API и указать его в одноименном свойстве элемента. Учтите, что сервис платный.

![](<../../../../.gitbook/assets1/linux_items-extra/2captcha-api-key.png>)




## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Ключ сайта\*** *[String]* — ключ капчи reCAPTCHA v2. Пример: `"6LfW6wATAAAAAHLqO2pb8bDBahxlMxNdo9g947u9"`.
1. **Ключ API\*** *[String]* — ключ API. Пример: `"7a17bf3f570f76e2140b7e9ce2c00000"`.
1. **URL API\*** *[String]* — URL API. Пример: `"https://2captcha.com"`.
1. **URL\*** *[String]* — URL страницы с капчей. Пример: `"https://recaptcha-demo.appspot.com/recaptcha-v2-checkbox.php"`.
1. **Невидимая** *[Boolean]* — признак невидимой капчи. По умолчанию не используется.
1. **Тайм-аут\*** *[Int32]* — тайм-аут, указывается в миллисекундах. По умолчанию `20000`.
1. **Результат** *[String]* — название переменной, в которую будет сохранен результат разбора капчи.




