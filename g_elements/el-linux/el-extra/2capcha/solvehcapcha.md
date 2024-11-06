# Решить hCapcha

![](<../../../../.gitbook/assets1/linux_items/library/hcapcha.png>)

Элемент решает капчу формата hCapcha. Этот вид капчи похож на reCAPTCHA и выглядит следующим образом:

![](<../../../../.gitbook/assets/image (801).png>)

Принцип решения капчи довольно прост:

1. Найдите в исходном коде страницы значение параметра _data-sitekey_.
2. Поместите его в свойство элемента **Ключ сайта**.
3. Поместите полученный токен в скрытые элементы _h-captcha-response_ и _g-recaptcha-response_ и отправьте форму.


## Начальные условия

1. [Установите](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio-linux/projects/manage-dependencies#menedzher-zavisimostei) пакет Primo.2Captcha.Linux в Primo RPA Studio версии 1.24.8.2 и выше.
1. Зарегистрируйтесь на сайте https://2captcha.com, чтобы получить ключ API и указать его в одноименном свойстве элемента. Учтите, что сервис платный.

![](<../../../../.gitbook/assets1/linux_items/library/2captcha-api-key.png>)




## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Ключ сайта\*** *[String]* — ключ hCapcha. Пример: `"a5f74b19-9e45-40e0-b45d-47ff91b7a6c2"`.  
1. **URL\*** *[String]* — URL сайта с капчой. Пример: `"https://accounts.hcaptcha.com/demo"`.
1. **Ключ API\*** *[String]* — ключ API. Пример: `"aa7a17bf3f570f76e0000b7e9ce2c65905"`.
1. **URL API\*** *[String]* — URL API. Пример: `"https://2captcha.com"`.
1. **Тайм-аут\*** *[Int32]* — тайм-аут, значение указывается в миллисекундах. По умолчанию `20000`.
1. **Результат** *[String]* — название переменной для хранения полученного разбора капчи.





