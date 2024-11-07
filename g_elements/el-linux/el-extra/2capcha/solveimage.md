# Решить изображение

![](<../../../../.gitbook/assets1/linux-items-extra/solveimage.png>)

Элемент решает простую капчу, представляющую собой текст в изображении. Результат сохраняется в указанную переменную.

Простая капча — это изображение, на котором размещён искажённый текст, который может быть прочитан человеком. Чтобы решить капчу, нужно ввести текст с изображения.

![](<../../../../.gitbook/assets1/linux-items-extra/normal-captcha.png>)


## Начальные условия

1. [Установите](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio-linux/projects/manage-dependencies#menedzher-zavisimostei) пакет Primo.2Captcha.Linux в Primo RPA Studio версии 1.24.8.2 и выше.
1. Зарегистрируйтесь на сайте https://2captcha.com, чтобы получить ключ API и указать его в одноименном свойстве элемента. Учтите, что сервис платный.

![](<../../../../.gitbook/assets1/linux_items-extra/2captcha-api-key.png>)

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Ключ API** *[String]* — ключ API.
1. **URL API** *[String]* — URL API.
1. **URL изображения** *[String]* — URL изображения.
1. **Изображение** *[System.Drawing.Bitmap]* — изображение.
1. **Язык** *[String]* — язык вопроса.
1. **Тайм-аут** *[Int32]* — тайм-аут. По умолчанию `` миллисекунд.
1. **Результат** *[String]* — результат разбора капчи.



## Только код

Данный элемент не используется в процессе с типом **Только код** (Pure code).
