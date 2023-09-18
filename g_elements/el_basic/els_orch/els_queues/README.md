# Очереди

Раздел описывает возможные операции с элементами очереди Оркестратора. 

Очередь — это контейнер данных в хранилище Оркестратора. Очереди позволяют организовать взаимодействие Студии и роботов Оркестратора при выполнении RPA-проектов.

Элемент очереди\* - это информация, которая была получена Роботом при выполнении RPA-проекта. Позднее ее могут использовать другие роботы Оркестратора.

Очередь позволяет хранить неограниченное количество элементов (данных).

> \**Часто вместо понятия **Элемент очереди** употребляется слово **Транзакция**. Эти термины равнозначны.*

## Как работать с очередью

RPA-разработчики управляют очередями при помощи следующих элементов Студии:

* [Добавить в очередь](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/addtoqueue)
* [Получить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/readfromqueue)
* [Получить из очереди по ID](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/peekqueueid)
* [Получить из очереди по фильтру](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/peekqueuefilter)
* [Ожидать сообщения из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/waitqueue)
* [Изменить статус в очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/changestatequeue)
* [Удалить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/deletequeueitem)

Их можно найти на панели **Элементы** в группе **Оркестратор ➝ Очереди**, как показано на рисунке ниже:

![](<../../../../.gitbook/assets/очереди орк. панель-2.png>)

## Требование

Для работы с этими компонентами [Оркестратор должен быть связан с Роботом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/register-robot).

### Дополнительно

О том, как создать очередь в Оркестраторе, читайте [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues).



