# Ожидать сообщения из очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (72).png>)

![](<../../../../.gitbook/assets/ожидать сообщения из очереди.png>)

Компонент, ожидающий элемент очереди (сообщение) из Оркестратора.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство  | Тип                                                                                                                                             | Описание                                                                         |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Очередь\* | String                                                                                                                                          | Название очереди в Оркестраторе                                                  |
| Период    | Int32                                                                                                                                           | Период опроса очереди (мс)                                                       |
| Элемент   | [LTools.Enterprise.Model.QueueItem](https://github.com/ttalantseva/Docs.Rus/blob/main/g\_elements/el\_basic/els\_orch/els\_queues/datatypes.md) | Переменная, которая будет хранить полученный элемент очереди в виде объекта      |
| Таблица   | DataTable                                                                                                                                       | Переменная, которая будет хранить полученный элемент очереди в формате DataTable |
| Результат | String                                                                                                                                          | Переменная, которая будет хранить полученный элемент очереди в формате String    |
