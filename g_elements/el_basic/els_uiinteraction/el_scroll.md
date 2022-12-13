# Прокрутка

![](<../../../.gitbook/assets/image (483).png>)

Элемент, осуществляющий прокрутку в визуальном компоненте.

| Свойство             | Тип                                  | Описание                                            |
| -------------------- | ------------------------------------ | --------------------------------------------------- |
| Шаблон поиска        | String                               | Шаблон поиска элемента управления                   |
| Элемент              | LTools.UIInteraction.Model.UIControl | Ссылка на элемент управления                        |
| Горизонтальная       | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)? | Горизонтальная прокрутка (%)   |
| Вертикальная         | double?                              | Вертикальная прокрутка (%)                          |
| Прокрутка            | [System.Drawing.Point](https://learn.microsoft.com/ru-ru/dotnet/api/System.Drawing.Point?view=netcore-1.1)                 | Текущее состояние прокрутки                         |
| Область              | [System.Drawing.Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=netcore-3.0)   | Область поиска компонента                           |
| Текущий пользователь |                                      | Искать только среди процессов текущего пользователя |
| Таймаут\*            | Int32                                | Предельное время ожидания завершения процесса (мс)  |

> Символ ? в типе данных указывает на то, что значение может быть null.
