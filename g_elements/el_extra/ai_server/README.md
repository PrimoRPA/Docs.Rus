# AI.Server

Библиотека **Primo.AI.Server** реализована для взаимодействия с решением Primo RPA AI Server. Библиотека содержит набор элементов для разработки RPA-проекта, ключевой задачей которого является получение результатов распознавания новых изображений обученной моделью. 

В библиотеку входят элементы:
* [Сервер Primo.AI](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/primoaiserver) — производит подключение к Primo RPA AI Server, а также выполняет роль контейнера для других элементов из библиотеки Primo.AI.Server.
* [Создать запрос](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/createrequest) — отправляет запрос на распознавание документа в Primo RPA AI Server.
* [Получить результат](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult) — получает от Primo RPA AI Server результат распознавания документа обученной моделью нейронной сети.
* [Проверить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/validatedoc) — производит валидацию распознанных данных и позволяет скорректировать их.

Данный набор элементов будет доступен в Студии только после [установки библиотеки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei) **Primo.AI.Server**. Вы сможете увидеть их на панели элементов в группе **AI**.

![](<../../../.gitbook/assets1/windows_items/library/ai-server-group.png>)


## Порядок применения элементов

Процесс, разработанный с помощью элементов библиотеки **Primo.AI.Server**, может выглядеть так:

![](<../../../.gitbook/assets1/windows_items/rpa-flow-for-server-ai.png>)

Элемент **Wait** ([Ожидание](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/el_logic_wait)), не входящий в состав библиотеки, используется в данном примере, чтобы предоставить серверу больше времени для распознавания.
