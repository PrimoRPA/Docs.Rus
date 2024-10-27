---
description: Process documents
---

# Обработать документы

![](<../../../.gitbook/assets1/windows_items/library/WFProcessDocumentSrv.png>)

Элемент осуществляет обработку документов на сервере ContentCapture. Подключение к серверу настраивается в контейнере **Сервер ContentCapture**.


## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет Primo.OCR.ContentAI, иначе данный элемент будет недоступен.


## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**

1. **Проект\*** *[String]* — имя проекта.
1. **Пакет\*** *[String]* — имя пакета.
1. **Документ** *[String]* — путь к файлу обрабатываемого документа.
1. **Пакет документов** *[List\<string\>]* — массив путей к файлам документов.
1. **Удалять пакет** *[Boolean]* — удалять пакет по завершении обработки.
1. **Асинхронный** *[Boolean]* — признак асинхронной обработки документов.
1. **Пакет** *[Primo.OCR.ContentAI.Model.BatchInfo]* — информация о пакете.
1. **Свойства** *[List\<Dictionary\<string, string\>\>]* — свойства документа.
1. **Таймаут\*** *[Int32]* — максимальное время ожидания завершения процесса (мс).
1. **Использовать User ID** *[Boolean]* — использовать User ID.
1. **Игнорировать размер** *[Boolean]* — игнорировать размеры файлов.

**Вывод:**

1. **Результат** *[Primo.OCR.ContentAI.Model.RecognitionResults]* — результат обработки документов.
1. **Пакет** *[Primo.OCR.ContentAI.Model.BatchInfo]* — информация о пакете.


Primo.OCR.ContentAI.Model.RecognitionResult - Свойства:
  - [string (имя поля)] [string]: Данные поля
  - [int (индекс)] [KeyValuePair<string, string>?]: Данные поля (ключ - имя поля, значение - данные поля)
  - Fields [Dictionary<string, string>]: Массив полей (ключ - имя поля, значение - значение поля)
  - Tables [Dictionary<string, List<Dictionary<string, string>>>]: Массив таблиц (ключ - имя таблицы, значение - массив таблиц)
  - TemplateName [string]: Имя шаблона
  - State [string]: Статус результата обработки


