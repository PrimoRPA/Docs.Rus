# Присутствие элемента

![](<../../../.gitbook/assets/image (571).png>)

Компонент, производящий поиск элемента управления.

| Свойство             | Тип                                         | Описание                                              |
| -------------------- | ------------------------------------------- | ----------------------------------------------------- |
| Шаблон поиска\*      | String                                      | Шаблон поиска элемента управления                     |
| Элемент              | LTools.UIInteraction.Model.UIControl        | Переменная для хранения ссылки на элемент управления  |
| Элементы             | List\<LTools.UIInteraction.Model.UIControl> | Переменная для хранения ссылок на элементы управления |
| Результат            | Boolean                                     | Переменная, хранящая результаты поиска                |
| Область              | System.Drawing.Rectangle                    | Область поиска компонента                             |
| Текущий пользователь |                                             | Искать только среди процессов текущего пользователя   |
| Таймаут\*            | Int32                                       | Предельное время ожидания завершения процесса (мс)    |
