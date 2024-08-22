---
description: Primo.AI server
---

# Сервер Primo.AI

Элемент производит подключение к серверу Primo RPA AI Server. Элемент выполняет роль контейнера для других компонентов, работающих с Primo RPA AI Server, а именно:
* для элемента **Создать запрос**;
* для элемента **Получить результат**.

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)

## Перед началом работы

Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Сервер** *[String]* — адрес сервера. Пример: `"https://ip:port/"`
2. **Тайм-аут** *[Int32]* — предельное время ожидания действий сервера, указывается в миллисекундах. По умолчанию `30000`. 
