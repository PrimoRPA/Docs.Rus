# Получить результат NLP

![](<../../../../.gitbook/assets1/windows_items/library/Primo.AI.Server.Elements.WFPrimoAIGetRequestNlp.png>)

Элемент получает от Primo RPA AI Server результат обработки NLP-запроса. Результат сохраняется в переменную, указанную в свойствах элемента.

Чтобы получить результат обработки, вам должен быть известен идентификатор отправленного ранее запроса. Если идентификатора нет, то сначала создайте NLP-запрос.

## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).
1. Найдите на панели элементов группу **AI > NLP** и перетащите элемент **Получить результат NLP** в процесс.
1. Убедитесь, что в контейнере **Сервер Primo.AI** верно настроены параметры подключения к серверу.



## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**
* **Ключ запроса\*** *[System.Guid]* — название переменной, в которой содержится идентификатор NLP-запроса.

**Вывод:**
* **Результат** *[Primo.AI.Server.Model.NlpResult]* — название переменной, в которую сохранится результат выполненного запроса.

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
