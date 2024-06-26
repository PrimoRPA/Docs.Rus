# Копирование диапазона

Элемент копирует диапазон ячеек ODF-таблицы для вставки в другой лист. Вставку возможно осуществить как внутри исходного файла, так и во внешний файл.

Путь до исходного файла указывается в контейнере «Таблица ODF». Путь до внешнего файла указывается в свойствах элемента «Копирование диапазона».

![Элемент «Копирование диапазона»](<../../../../.gitbook/assets1/windows_items/odf-copy-range.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон-источник\*** *[String]* — диапазон ячеек, который вы хотите скопировать. Диапазон можно указать в точности: `"A1:D12"` либо использовать символ `*` вместо столбца или номера строки, например: `"A1:*12"` или `"A1:D*"`.
2. **Диапазон-приемник\*** *[String]* — диапазон ячеек для вставки данных. Например, `"A1"` или `"A1:D12"`.
3. **Страница-источник** *[String]* — наименование страницы-источника данных.
4. **Индекс страницы-источника** *[Int32]* — номер страницы-источника. Нумерация с нуля.
5. **Страница-приемник** *[String]* — наименование страницы-приемника данных.
6. **Индекс страницы-приемника** *[Int32]* — номер страницы-приемника. Нумерация с нуля.
7. **Формат** — определяет формат, в котором следует скопировать данные. Доступны следующие значения:
   * *All* — будут скопированы все значения, форматы и формулы из диапазона. Значение по умолчанию.
   * *Values* — будут скопированы только значения. Формат ячеек и формулы будут проигнорированы — вместо формул подставится готовый результат.
   * *Formulas* — будут скопированы значения и формулы. Чтобы значение формул корректно отображалось при вставке, добавьте после копирования диапазона компонент [Пересчет формул](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/odf_oxml/table/odf_calculate).
   * *Formats* — будет скопирован только формат ячеек, шрифт и цвета. Значения и формулы проигнорируются.
8. **Путь к документу** *[String]* — путь к внешнему файлу, в который необходимо вставить скопированный диапазон. Если он не задан, диапазон будет вставлен внутри файла-источника.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.CopyRange(range, rangeTo, [sheet], [sheetIdx], [sheetTo], [sheetIdxTo], [format], [file]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
