# AI.Server

**Primo.AI.Server** — пакет NuGet, который предназначен для взаимодействия с сервисом Primo RPA AI Server. Пакет содержит набор элементов для разработки RPA-проекта, цель которого — обработать изображение документа или текст на естественном языке с помощью модели нейросети.

Пакет составляют элементы:
* [Сервер Primo.AI](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/primoaiserver) — производит подключение к AI Server, а также выполняет роль контейнера для других элементов из библиотеки Primo.AI.Server.
* группа **Умный OCR**:
  * [Создать запрос OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/createrequest) — отправляет запрос на распознавание иображения документа в AI Server.
  * [Получить результат OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult) — получает от AI Server результат распознавания документа обученной моделью.
  * [Проверить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/validatedoc) — производит валидацию распознанных данных и позволяет скорректировать их.
* группа **NLP**:
  * Создать запрос NLP — отправляет запрос для обработки текста на естественном языке с помощью LLM-модели. 
  * Получить результат NLP — получает результат NLP-запроса по его идентификатору.

После установки библиотеки в Primo RPA Studio, на панели элементов появится группа **AI**:

![](<../../../.gitbook/assets1/windows_items/library/ai-server-items.png>)


## Порядок применения элементов

Процесс с элементами группы **Умный OCR** может выглядеть так:

![](<../../../.gitbook/assets1/windows_items/rpa-flow-for-server-ai.png>)

Элемент **Wait** ([Ожидание](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/el_logic_wait)) не входит в состав библиотеки и используется в данном примере, чтобы предоставить серверу больше времени для распознавания.
