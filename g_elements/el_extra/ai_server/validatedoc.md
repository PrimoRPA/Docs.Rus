---
description: Validate document
---

# Проверить документ

## Перед началом работы

Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.

## Описание элемента

![](<../../../.gitbook/assets1/windows_items/validate-doc.png>)

Элемент **Проверить документ** проверяет результат распознавания документа. Результат распознавания в данном контексте — это переменная с типом `Primo.AI.Server.Model.InferenceResult`, которую получают с помощью элемента [Получить результат](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult). 

Элемент **Проверить документ** валидирует содержимое этой переменной и сохраняет результат валидации в новую переменную с тем же типом данных. Во время валидации открывается диалоговое окно с изображением документа и распознанными полями:
* *Зеленым цветом выделены успешно распознанные блоки.*
* *Желтым либо красным — требующие внимания.*

:large_orange_diamond:***Важно**. Если вы запустили отладку процесса в Студии, проверьте состояние параметра **Сворачивать Студию** [в настройках приложения](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#otladchik). Если Студия не сворачивается, то сверните приложение самостоятельно, чтобы увидеть окно валидации.*

![](<../../../.gitbook/assets/image (18).png>)

Окно валидации предоставляет возможность изменить данные, требующие корректировки. Для этого выберите нужный блок на изображении и скорректируйте данные в самом блоке, либо в нижней панели. Для перемещения между блоками также можно использовать кнопки слева от панели редактирования.

Для завершения редактирования нажмите кнопку ![](<../../../.gitbook/assets/image (148) (1) (2) (1) (1) (2) (1).png>)



## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**

1. **Документ\*** *[String]* — путь к файлу обрабатываемого документа.
1. **Результат распознавания\*** *[[Primo.AI.Server.Model.InferenceResult](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#inferenceresult)]* — название переменной с результатом распознавания документа.

**Вывод:**

**Результат обработки** *[Primo.AI.Server.Model.InferenceResult]* — название переменной, в которую сохранится проверенный результат распознавания.


