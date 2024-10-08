---
description: Create request
---

# Создать запрос

Элемент отправляет запрос на распознавание документа в Primo RPA AI Server. Используется в контейнере [**Сервер Primo.AI**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/primoaiserver).

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)

## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.

2. Подготовьте изображение, соответствующее следующим требованиям:
   * Поддерживаемые форматы файлов: JPEG, JPG, JPE, PNG, PDF, BMP, TIF, TIFF, DIB. 
   * Максимальный размер файла: ограничения отсутствуют.
   * Качество: 200 DPI при реальном размере изображения. Например, лист А4 - примерно 11 x 8 дюймов, т.е. 2200 x 1600 пикселей.
   * Размер изображения не должен превышать 20 мегапикселей (длина × ширина).
   * Количество страниц: одностраничный документ. Многостраничные документы необходимо разбить на отдельные страницы и распознавать постранично.

Подробнее с требованиями можно ознакомиться [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/other/inference-quality-requirements).

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Обработка:

1. **Документ\*** *[String]* — путь к документу для распознавания. Например, создайте в RPA-проекте папку `Data`, разместите в ней файл и укажите в данном свойстве путь: `System.IO.Path.Combine(_Workflow.ProjectPath,"Data","название_файла.расширение")`. 
2. **Тип модели** *[String]* — название типа модели, который будет обрабатывать документ. Должно совпадать с названием в Primo RPA AI Server, регистр важен. Пример: `"torg12"`.

#### Вывод:

* **Результат** *[System.Guid]* — название переменной, в которую будет сохранен идентификатор запроса на сервере. Идентификатор генерируется автоматически. Позже его можно использовать в элементе **Получить результат**.

> *Если в ответе на запрос сервер вернул ошибку, она будет выведена в [консоль](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#konsol) Студии.*
