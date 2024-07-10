# Primo.AI.Server

Библиотека **Primo.AI.Server** реализована для взаимодействия с решением Primo RPA AI Server. Библиотека содержит набор элементов для разработки RPA-проекта, ключевой задачей которого является получение результатов распознавания новых изображений обученной моделью. 

В библиотеку входят элементы:
* [Сервер Primo.AI](https://github.com/PrimoRPA/Docs.Rus/blob/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server/primoaiserver.md) — производит подключение к Primo RPA AI Server, а также выполняет роль контейнера для других элементов из библиотеки Primo.AI.Server.
* [Создать запрос](https://github.com/PrimoRPA/Docs.Rus/blob/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server/createrequest.md) — отправляет запрос на распознавание документа в Primo RPA AI Server.
* [Получить результат](https://github.com/PrimoRPA/Docs.Rus/blob/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server/getresult.md) — получает от Primo RPA AI Server результат распознавания документа обученной моделью нейронной сети.
* [Проверить документ]() — производит валидацию распознанных данных и позволяет скорректировать их.

Данный набор элементов будет доступен в Студии только после [установки библиотеки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei) **Primo.AI.Server**. Вы сможете увидеть их на панели элементов в группе **AI**.

![](<../../../.gitbook/assets1/windows_items/library/ai-server-group.png>)


## Порядок применения элементов

Проект, выполненный с помощью элементов библиотеки **Primo.AI.Server**, может выглядеть так:

![](<../../../.gitbook/assets1/windows_items/rpa-flow-for-server-ai.png>)
