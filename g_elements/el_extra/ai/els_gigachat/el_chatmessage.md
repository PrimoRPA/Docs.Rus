# Вопрос в чат

Отправляет ваш вопрос в сервис GigaChat.

![](<../../../../.gitbook/assets1/сбер токен.png>)

Элемент становится доступным только при установке библиотеки **Primo.AI**. Найти его можно в группе элементов GigaChat на соответствующей панели:

![](<../../../../.gitbook/assets1/gigachat-on-panel.png>)

В переменной вывода вернется ответ от нейросетевой модели.


## Предварительные условия

Для успешной отправки вопроса сначала следует [получить токен](https://github.com/PrimoRPA/Docs.Rus/blob/1134-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D0%B0-ai/g_elements/el_extra/ai/els_gigachat/el_gettoken.md). Токен действует в течение 30-ти минут, после чего его потребуется обновить.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**GigaChat**:

1. **Творчество\*** *[Double]* - творческая составляющая ответа (от 0 до 1).  
1. **Тайм-аут\*** *[Int32]* - максимальное время ожидания выполнения запроса. Указывается в миллисекундах, по умолчанию `20000`.

**Запрос**:

1. **Токен\*** *[String]* - токен запроса. Указывается в виде переменной или константы.
1. **Вопрос\*** *[String]* - текст вопроса.
1. **Роль\*** *[String]* - имя роли в чате. По умолчанию `"user"`.

**Вывод**:
* **Ответ** *[String]* - переменная для хранения ответа GigaChat. 

Пример заполнения свойств:

![](<../../../../.gitbook/assets1/сбер свойства вопрос.png>)

## Просмотр ответа

Чтобы просмотреть ответ GigaChat, установите [точку останова](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#tochka-ostanova), запустите [отладку](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug) процесса и на панели [**Вывод**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#panel-vyvod) откройте текущее значение переменной:

![](<../../../../.gitbook/assets1/сбер переменная ответа.png>)

Пример отладки процесса с записью ответа в консоль:

![](<../../../../.gitbook/assets1/сбер отладка.png>)

## Полезные материалы

* [Как формулировать запросы к GigaChat](https://developers.sber.ru/help/gigachat/prompt-guide);
* [Примеры удачных запросов](https://developers.sber.ru/help/gigachat/prompt-examples);
* [Ответы на общие вопросы о GigaChat](https://developers.sber.ru/help/gigachat/faq).



