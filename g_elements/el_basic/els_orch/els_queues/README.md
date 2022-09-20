# Очереди

Раздел описывает возможные действия с элементами очереди Оркестратора. 

Очередь — это контейнер данных в хранилище Оркестратора. Очереди позволяют организовать взаимодействие Студии и Роботов Оркестратора при выполнении RPA-проектов.
Элемент очереди - это информация, которая была получена Роботом при выполнении RPA-проекта. Позднее ее могут использовать другие Роботы Оркестратора.

> *Часто понятие **Элемент очереди** может замещаться в Студии словами **Значение** или **Сообщение**. Значение - это данные элемента очереди, одно из свойств [объекта QueueItem](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/datatypes)*.

Очередь позволяет хранить неограниченное количество элементов (данных). Данные обрабатываются в очереди по принципу **первым пришёл – первым обслужен**.

## Как работать с Очередью

Управление очередями осуществляют разработчики RPA при помощи следующих элементов Студии:

* [Добавить в очередь](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/addtoqueue)
* [Получить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/readfromqueue)
* [Получить из очереди по ID](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/peekqueueid)
* [Получить из очереди по фильтру](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/peekqueuefilter)
* [Ожидать сообщения из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/waitqueue)
* [Изменить статус очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/changestatequeue)
* [Удалить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/deletequeueitem)

Их можно найти на панели **Элементы** в группе **Оркестратор ➝ Очереди**, как показано на рисунке ниже:

![](<../../../../.gitbook/assets/очереди орк. панель.png>)

## Требование

Для работы с этими действиями [Оркестратор должен быть связан с Роботом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/register-robot).

### Дополнительно

О том, как создать очередь в Оркестраторе, читайте [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues).



