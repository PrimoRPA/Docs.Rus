---
description: Get result
---

# Получить результат OCR

![](<../../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)

Элемент получает результат обработки документа по идентификатору OCR-запроса. 


## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).
1. Поместите элемент **Получить результат OCR** в контейнер **Сервер Primo.AI**. 


## Свойства
Обязательные свойства отмечены символом `*`. Описание общих свойств см. в [этом разделе](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — идентификатор запроса к Primo RPA AI Server. Получить его можно в результате выполнения элемента [Создать запрос OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/ocr/createrequest).
1. **Результат** *[[Primo.AI.Server.Model.InferenceResult](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/ocr/datatypes/inferenceresult)]* — название переменной, в которую сохранится результат обработки документа. 



