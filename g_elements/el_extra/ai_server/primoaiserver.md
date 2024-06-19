---
description: Primo.AI server
---

# Сервер Primo.AI

Элемент производит подключение к серверу Primo RPA AI Server. Выполняет роль контейнера для других элементов, работающих с Primo RPA AI Server, а именно:
* для элемента «Создать запрос»;
* для элемента «Получить результат».

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Сервер** *[String]* — URL сервера. Пример: `"https://ip:port/"`
2. **Тайм-аут** *[Int32]* — предельное время ожидания действий сервера, указывается в миллисекундах. По умолчанию `30000`. 
