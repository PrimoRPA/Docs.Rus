# Автофильтры

Элемент управляет [автофильтрами](https://support.microsoft.com/ru-ru/office/%D1%84%D0%B8%D0%BB%D1%8C%D1%82%D1%80%D0%B0%D1%86%D0%B8%D1%8F-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85-%D0%B2-%D0%B4%D0%B8%D0%B0%D0%BF%D0%B0%D0%B7%D0%BE%D0%BD%D0%B5-%D0%B8%D0%BB%D0%B8-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B5-01832226-31b5-4568-8806-38c37dcc180e) в книге Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

Чтобы изменения применились, в конце работы c файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](<../../../.gitbook/assets1/windows_items/ExcelWFAutoFilter.png>)


## Свойства

Символ `*` в названии указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Excel**:

1. **Страница** *[String]* — название страницы в книге Excel. Пример: `"List1"`.
1. **Индекс страницы** *[Int32]* — порядковый номер листа в книге Excel. Нумерация начинается с нуля. Если указан индекс, то страница в файле может быть переименована. Пример: `0`.
1. **Режим** — устанавливаемый режим автофильтров. Доступные значения:
   * *None* — режим не выбран. Значение по умолчанию.
   * *Re Apply* — применить повторно автофильтры.
   * *Disabled* — отключить автофильтры.


**Вывод**:

1. **Текущий** *[System.Boolean]* — текущий режим автофильтров.
