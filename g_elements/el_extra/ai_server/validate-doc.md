---
description: Validate
---

# Проверить документ

Элемент выполняет валидацию распознавания документа. Используется вне контейнера

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)


## Перед началом работы

Убедитесь, что в Студии установлена библиотека [Primo.AI.Server](https://github.com/PrimoRPA/Docs.Rus/tree/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Документ\*** *[String]* — путь к файлу обрабатываемого документа.
1. **InferenceResult** *[Primo.AI.Server.Model.InferenceResult]* — название переменной для сохранения данных проверки.
