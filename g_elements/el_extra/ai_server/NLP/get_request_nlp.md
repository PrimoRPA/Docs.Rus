# Получить результат NLP

Элемент получает результат обработки NLP-запроса от Primo RPA AI Server.


## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).
1. Найдите на панели элементов группу **AI > NLP** и перетащите элемент **Получить результат NLP** в свой процесс.
1. Убедитесь, что в контейнере **Сервер Primo.AI** верно настроены параметры подключения к серверу.
1. Для успешного использования элемента **Получить результат NLP** вам должен быть известен идентификатор отправленного NLP-запроса. Если его нет, то сначала создайте NLP-запрос и сохраните полученный идентификатор запроса в переменную.



## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**
* **Ключ запроса\*** *[System.Guid]* — название переменной, в которой содержится ключ отправленного NLP-запроса.

**Вывод:**
* **Результат** *[Primo.AI.Server.Model.NlpResult]* — название переменной, в которую сохранится результат запроса.

Primo.AI.Server.Model.NlpResult - Свойства:
  - CreatedAt [System.DateTimeOffset]: Дата создания запроса
  - ExpiresAt [System.DateTimeOffset]: Дата, до которой хранятся все данные запроса
  - RoutingKey [String]: Ключ маршрутизации
  - Key [Guid]: Ключ запроса
  - Result [Primo.AI.Server.Model.NlpResultContent]: Результат

Primo.AI.Server.Model.NlpResultContent - Свойства:
  - StreamingStartedAt [System.DateTimeOffset]: Дата и время получения первого фрагмента результата
  - UpdatedAt [System.DateTimeOffset]: Дата и время последнего обновления ответа
  - StreamingCompletedAt [System.DateTimeOffset]: Дата и время завершения генерации результата
  - IsReady [System.DateTime]: Флаг готовности результата
  - IsFailed [String]: Флаг ошибочной обработки запроса
  - Answer [String]: Текст ответа
  - ErrorMsg [String]: Текст ошибки
