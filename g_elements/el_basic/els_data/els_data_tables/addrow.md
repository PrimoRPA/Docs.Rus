# Добавить строку

*Eng: AddRow*

Добавляет строку в существующую таблицу.

![](<../../../../.gitbook/assets/image (345).png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

:small_blue_diamond: Обязательными к заполнению являются свойство **Таблица** и один из типов **Строки**.

1. **Таблица\*** [[`System.Data.DataTable`](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-8.0&viewFallbackFrom=net-4.6.1)] - объект DataTable. Представляет собой редактируемую таблицу, в которую будут добавлены строки.
1. **Строка (справочник)** [`Dictionary<String, Object>`] - свойство используется для создания новых строк в таблице. Представляет собой словарь, где ключ - это имя колонки, а значение - это значение ячейки.
1. **Строка (List)** [`System.Collections.Generic.List<Object>`] - cписок объектов, который используется для создания новых строк в таблице.
1. **Строка (DataRow)** [[`System.Data.DataRow`](https://docs.microsoft.com/ru-ru/dotnet/api/system.data.datarow?view=net-4.6.1)] - объект DataRow, который используется для создания новых строк в таблице.



##  Learning
Пример работы с элементом **Добавить строку** вы можете скачать по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).

Распакуйте архив и откройте проект `StudioActivities` в вашей среде разработки.

Найдите процесс `StudioActivities/Ru/Данные/Таблицы/Таблицы.ltw` для просмотра.
