---
description: Run macro
---

# Запустить макрос


Элемент выполняет макрос Excel. Поддерживает работу только с драйвером Interop. Драйвер указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

Макросы — это команды, записанные на языке VBA (Visual Basic for Applications). Они используются для автоматизации часто повторяющихся действий в Excel. 

Перед выполнением элемента убедитесь, что в Excel [включены макросы](https://support.microsoft.com/ru-ru/office/%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2-%D0%B1%D0%B5%D0%B7%D0%BE%D0%BF%D0%B0%D1%81%D0%BD%D0%BE%D1%81%D1%82%D0%B8-%D0%BC%D0%B0%D0%BA%D1%80%D0%BE%D1%81%D0%BE%D0%B2-%D0%B2-excel-a97c09d2-c082-46b8-b19f-e8621e8fe373). В конце работы рекомендуем использовать элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/el_excel_save), чтобы все изменения применились.

![](<../../../.gitbook/assets1/WFRunMacro-right.png>)



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип           | Описание             |
| -------------- | ------------- | -------------------- |
| ***Excel***    |               |                      |
| Наименование\* | String        | Имя макроса. Указывается без названия файла, в котором он находится     |
| Аргументы\*    | List\<object> | Входные значения макроса. Можно передавать до 10 аргументов |
| Видимость\*    | Boolean       | Видимость Excel. По умолчанию чекбокс отключен — приложение Excel не отображается на экране |
| Асинхронный    | Boolean       | Признак асинхронного выполнения. По умолчанию чекбокс отключен — макрос выполняется синхронно |
| Тайм-аут       | int           | Предельное время выполнения макроса (мс). По умолчанию тайм-аут не задан |
| ***Вывод***    |               |                      |
| Переменная     | Object        | Переменная, которая будет хранить результат выполнения скрипта  |

Пример заполненных свойств:

![](<../../../.gitbook/assets1/WFRunMacro-parameters.png>)


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExample**.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.RunMacro("macro", null, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.RunMacro("macro", null, true)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.RunMacro("macro", null, true);
```
{% endtab %}
{% endtabs %}
