---
description: Set focus
---

# Фокус ввода

![](<../../../.gitbook/assets/image (456).png>)

Устанавливает фокус ввода на выбранном элементе управления.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                  | Описание                                            |
| -------------------- | ------------------------------------ | --------------------------------------------------- |
| Шаблон поиска        | String                               | [Шаблон поиска](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns) элемента управления |
| Элемент              | [LTools.UIInteraction.Model.UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/tipy-dannykh/uicontrol) | Ссылка на элемент управления |
| Область              | [System.Drawing.Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=netcore-3.0)   | Область поиска компонента                        |
| Текущий пользователь | Boolean                              | Искать только среди процессов текущего пользователя |
| Прокрутить до видимости | Boolean   | Cвойство при активации автоматически прокручивает страницу до того момента, когда целевой элемент становится видимым на экране, перед выполнением действия. Если опция отключена, действия будут выполняться без предварительной прокрутки. ***Функция доступна с версии 1.24.10***
| Таймаут\*            | Int32                                | Предельное время ожидания завершения процесса (мс)  |
| Строгий таймаут      | Boolean                              | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. Рекомендуется использовать, когда требуется строгое соблюдение временного ограничения. |
