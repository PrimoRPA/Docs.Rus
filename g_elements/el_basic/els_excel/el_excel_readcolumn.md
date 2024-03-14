---
description: Read column
---


# Чтение колонки

Элемент считывает данные из указанного столбца. 

![](<../../../.gitbook/assets/excel-read-column.png>)

**Примечания**:

1. Путь до файла, тип драйвера и другие параметры подключения настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Элемент **Чтение колонки** размещается внутри контейнера.
2. Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                         |
| -------------------- | --------------------- | -------------------------------- |
| **Excel:**  | |  |
| Ячейка\*             | String   | Идентификатор начальной ячейки. Пример: `"A4"`  |
| Страница             | String   | Название страницы, где находится колонка с данными. Пример: `"Лист 1"` |
| Индекс страницы      | Int32    | Порядковый номер страницы с колонкой. Отсчет ведется с 0. Пример: `0` |
| **Вывод:**  | |  |
| Данные\*             | List\<Object\> | Переменная, в которой будут храниться данные, полученные из колонки |

**Пример заполненных свойств**:

![](<../../../.gitbook/assets/excel-read-column2.png>)

## Пример использования
RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExamples**.


## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell- Ячейка: [String] Идентификатор ячейки (A1), с которой начинается чтение
//data - Данные: [List<Object>] Данные в формате списка объектов
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\columns-rows.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
String cell="A2";
List<Object> data = app.ReadColumn(cell,"Лист1",0);
		
foreach (object value in data)
{
    LTools.Workflow.PrimoApp.AddToLog(wf, value.ToString(), LTools.Enums.LogMessageType.Info);
}
```
{% endtab %}
