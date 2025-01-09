---
description: Chat question (Linux)
---

# Вопрос в чат

Элемент позволяет отправить вопрос в сервис GigaChat.

## Перед началом работы

Библиотека Primo.AI.Linux не включена в стандартный набор и требует установки [Primo.AI.Linux](https://www.nuget.org/packages/Primo.AI.Linux). 
Установку можно выполнить двумя способами:

**1. Через сайт NuGet:**
   Загрузите пакет по ссылке: [Primo.AI.Linux на NuGet.org](https://www.nuget.org/packages/Primo.AI.Linux).

**2. Через управление зависимостями в Primo RPA Studio**:

   - Откройте Primo Studio и перейдите в меню Настройки → Управление зависимостями.
   - В списке источников выберите NuGet.org.
   - Найдите пакет Primo.AI.Linux с помощью поиска.
   - Установите или обновите пакет до последней версии.
   - Сохраните изменения и дождитесь завершения установки.

После установки библиотеки **Primo.AI.Linux** станут доступны группы элементов GigaChat и YandexGPT.


> Для корректной работы элемента укажите авторизационные данные клиента в свойствах. Подробные инструкции по получению авторизационных данных смотрите [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/ai#gigachat).

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**GigaChat**:

1. **Творчество\*** *[Double]* — творческая составляющая ответа. В значении укажите число от 0 до 1. Чем выше значение, тем более непредсказуемым будет результат выполнения запроса. По умолчанию `0.5`.
1. **Тайм-аут\*** *[Int32]* — максимальное время ожидания выполнения запроса. Указывается в миллисекундах, по умолчанию `20000`.

**Запрос**:

1. **Токен\*** *[String]* — токен запроса. Указывается в виде переменной или строки.
1. **Вопрос\*** *[String]* — текст вопроса.
1. **Роль\*** *[String]* — имя роли в чате. По умолчанию `"user"`.

**Вывод**:
1. **Ответ** *[String]* — переменная для хранения ответа GigaChat. 


## Просмотр ответа

Чтобы просмотреть ответ GigaChat, установите [точку останова](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#tochka-ostanova) и запустите [отладку](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug) процесса. На панели [**Вывод**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#panel-vyvod) откройте текущее значение переменной:

![](<../../../../.gitbook/assets1/сбер переменная ответа.png>)

Пример отладки процесса с записью ответа в консоль:

![](<../../../../.gitbook/assets1/сбер отладка.png>)

## Полезные материалы

* [Как формулировать запросы к GigaChat](https://developers.sber.ru/help/gigachat/prompt-guide);
* [Примеры удачных запросов](https://developers.sber.ru/help/gigachat/prompt-examples);
* [Ответы на общие вопросы о GigaChat](https://developers.sber.ru/help/gigachat/faq).
