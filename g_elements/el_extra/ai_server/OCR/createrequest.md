---
description: Create request
---

# Создать запрос OCR

![](<../../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)

Элемент отправляет запрос на распознавание документа в Primo RPA AI Server. Используется в контейнере [**Сервер Primo.AI**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/primoaiserver).


## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).
1. Подготовьте изображение документа в соответствии с требованиями:
   * Формат файла: JPEG, JPG, JPE, PNG, PDF, BMP, TIF, TIFF, DIB. 
   * Качество: 200 DPI при реальном размере изображения. Например, лист А4 — это ~ 11 x 8 дюймов, т.е. 2200 x 1600 пикселей.
   * Размер изображения не должен превышать 20 мегапикселей (длина × ширина).
   * Количество страниц: одностраничный документ. Многостраничные документы необходимо разбить на отдельные страницы и распознавать постранично.

Подробнее с требованиями можно ознакомиться [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/other/inference-quality-requirements).

## Свойства
Обязательные свойства отмечены символом `*`. Описание общих свойств см. в [этом разделе](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**

1. **Документ\*** *[String]* — путь к документу для распознавания. Например, создайте в RPA-проекте папку `Data`, разместите в ней файл, тогда путь будет: `System.IO.Path.Combine(_Workflow.ProjectPath,"Data","название_файла.расширение")`. 
2. **Тип модели** *[String]* — тип модели, который должен обработать документ. Название должно совпадать с названием типа модели в AI Server, регистр важен. Пример: `"torg12"`.

**Вывод:**

* **Результат** *[System.Guid]* — название переменной, в которую сохранится идентификатор запроса на сервере. Идентификатор генерируется автоматически. Позже его можно использовать в элементе **Получить результат**.

> *Если в ответе на запрос сервер вернул ошибку, она будет выведена в [консоль](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#konsol) Студии.*
