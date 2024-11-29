---
description: Get result
---

# Получить результат OCR

![](<../../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)

Элемент получает от Primo RPA AI Server результат обработки документа. Результат сохраняется в переменную, указанную в свойствах элемента.


## Перед началом работы

Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — идентификатор запроса к Primo RPA AI Server. Получить его можно в результате выполнения элемента [Создать запрос](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/createrequest).
1. **Результат** *[Primo.AI.Server.Model.InferenceResult]* — название переменной, в которую сохранится результат обработки документа. Описание модели InferenceResult представлено ниже.



