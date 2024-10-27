---
description: Get processing result
---

# Результаты обработки

![](<../../../.gitbook/assets1/windows_items/library/WFGetProcessResult.png>)

Элемент получает результат асинхронной обработки документов на сервере ContentCapture.


## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет Primo.OCR.ContentAI, иначе данный элемент будет недоступен.


## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).



**Обработка:**

1. **Пакет\*** *[Primo.OCR.ContentAI.Model.BatchInfo]* — информация о пакете.
1. **Удалять пакет** *[Boolean]* — удалять пакет по завершении обработки.
1. **Таймаут\*** *[Int32]* — максимальное время ожидания завершения процесса (мс)


**Вывод:**

1. **Результат** *[Primo.OCR.ContentAI.Model.RecognitionResults]* — результат обработки документов.

