# Очереди обмена данными

Очереди обмена данными – это структуры данных в хранилище Оркестратора, использующие принцип *Первым пришёл – первым обслужен* (FIFO). Очереди нужны для организации коммуникации Роботов и Студии при выполнении RPA-проектов. 

Кроме FIFO, Робот может обратиться к элементу напрямую по ключу – прочитать значение или удалить элемент очереди. Прямое обращение используется и для изменения статуса элемента на один из: *Завершилось успешно*, *Завершилось с ошибкой общего вида*, *Завершилось с бизнес-ошибкой*. Подробнее возможные действия с элементами очереди при помощи средств Студии описаны в разделе [Очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues).

Для создания очереди перейдите в раздел Оркестратора **Роботы ➝ Очереди обмена данными** и нажмите кнопку **Добавить очередь**:

![](<../../.gitbook/assets/0 (20)>)

Очередь может создаваться с дополнительными настройками:

| Параметр                                                          | Описание                                                                                    |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Время жизни элемента очереди (сек.)      | Время, после которого элемент принудительно удаляется из очереди |
| Максимальное количество попыток поставить элемент в очередь повторно  | Когда элемент очереди получает статус **Завершилось с ошибкой общего вида** или **Завершилось с бизнес-ошибкой**, он ставится в очередь по FIFO повторно. После превышения этого значения элемент в очередь повторно не ставится  |
| На какие ошибки элемент должен ставиться в очередь повторно  | **Завершилось с ошибкой общего вида** (Error) или **Завершилось с бизнес-ошибкой** (BusinessError) |
| Specific JSON Schema     | JSON-схемы, которым должен соответствовать элемент очереди  |
| Output JSON Schema       | см. выше  |
| Analytics JSON Schema    | см. выше |
| Робот может удалять только свои элементы | Робот по ключу сможет удалить только те элементы, которые он сам поместил в очередь |
| Зашифрована    | Определяет, будут ли элементы очереди храниться в БД в зашифрованном виде. По умолчанию элементы не шифруются |
| Публичная      | Очередь доступна либо всем роботам, либо только перечисленным  |

С дополнительными параметрами могут создаваться и элементы очереди. Чтобы добавить элемент через интерфейс Оркестратора, выделите нужную очередь и нажмите на количество элементов в ней - откроется раздел со списком элементов. Вверху страницы нажмите кнопку **Добавить элемент**: 

| Параметр                                                     | Описание                                                                                    |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Натуральный ключ | Содержательный идентификатор элемента очереди. Может быть глобальным в пределах очереди, в пределах всех очередей или уникальность может отсутствовать |
| Метаданные     | Словарь **Ключ-значение** с произвольными строковыми данными |
| Дата, до которой элемент считается недоступным     | Время, до которого откладывается обработка значения элемента Роботом |
| Дата, после которой элемент считается недоступным  | Время, после которого элемент будет удален из очереди  |
| Статус элемента очереди     | Текущий статус элемента в истории его статусов: *Успешно*, *Ошибка общего вида*, *Бизнес-ошибка* |
| Теги    | Произвольные строки, по которым может осуществляться поиск элементов |
