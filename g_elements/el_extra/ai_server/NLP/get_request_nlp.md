# Получить результат NLP

![](<../../../../.gitbook/assets1/windows_items/library/Primo.AI.Server.Elements.WFPrimoAIGetRequestNlp.png>)

Элемент получает результат обработки NLP-запроса от AI Server. Чтобы получить результат, укажите в свойствах элемента идентификатор запроса.

Поскольку результат может появиться не сразу, рекомендуется использовать элемент **Получить результат NLP** в цикле, а также добавлять в процесс элемент [Ожидание](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/el_logic_wait) (Wait).



## Перед началом работы

1. Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).
1. Найдите на панели элементов группу **AI > NLP** и перетащите элемент **Получить результат NLP** в процесс.
1. Убедитесь, что в контейнере **Сервер Primo.AI** верно настроены параметры подключения к серверу.



## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка:**
* **Ключ запроса\*** *[[System.Guid](https://learn.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-5.0)]* — название переменной, в которой содержится идентификатор NLP-запроса.

**Вывод:**
* **Результат** *[Primo.AI.Server.Model.NlpResult]* — название переменной, в которую сохранится результат выполненного запроса.




