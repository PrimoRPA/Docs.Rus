# Изменение шрифта

Элемент изменяет шрифт диапазона ячеек в Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

Чтобы изменения применились, в конце работы c файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](<../../../.gitbook/assets1/windows_items/ExcelWFSetFont.png>)


## Свойства

Символ `*` в названии указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон\*** *[String]* — диапазон ячеек. Пример: `"A1:D12"`.
1. **Страница** [String] — наименование страницы в книге Excel. Пример: `"List1"`.
1. **Индекс страницы** [Int32] — порядковый номер листа в книге Excel. Нумерация начинается с нуля. Если указан индекс, то страница в файле может быть переименована. Пример: `0`.
1. **Цвет** [System.Drawing.Color?] — цвет шрифта (System.Drawing.Color.Black).
1. **Размер** [double?] — размер шрифта.
1. **Полужирный** — полужирный.
1. **Наклонный** — наклонный.
1. **Подчеркнутый** — подчеркнутый.
