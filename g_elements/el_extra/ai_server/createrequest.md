---
description: Create request
---

# Создать запрос

Элемент создает запрос на распознавания документа к Primo RPA AI Server. Используется в рамках контейнера Сервер Primo.AI.

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Документ\*** *[String]* — путь к файлу обрабатываемого документа.
2. **Тип модели** *[String]* — тип модели для обработки документа.
3. **Результат** *[Primo.AI.Server.Model.ClassificationResult]* — результат создания запроса.
