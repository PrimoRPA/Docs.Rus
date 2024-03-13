---
description: Run macro
---

# Запустить макрос

Элемент выполняет макрос Excel. Поддерживает работу только с драйвером Interop. Драйвер указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

В конце работы с файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/el_excel_save), чтобы изменения применились.

![](<../../../.gitbook/assets1/WFRunMacro.png>)



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип           | Описание             |
| -------------- | ------------- | -------------------- |
| ***Excel***    |               |                      |
| Наименование\* | String        | Название макроса. Пример: `"BorderLine"`     |
| Аргументы\*    | List\<object> | Аргументы макроса. Можно передавать до 10 аргументов |
| Видимость\*    | Boolean       | Видимость Excel. По умолчанию чекбокс отключен — приложение Excel не отображается на экране |
| Асинхронный    | Boolean       | Признак асинхронного выполнения. По умолчанию чекбокс отключен — макрос выполняется синхронно |
| Тайм-аут       | int           | Предельное время выполнения макроса (мс). По умолчанию тайм-аут не задан |
| ***Вывод***    |               |                      |
| Переменная     | Object        | Переменная, которая будет хранить результат выполнения скрипта  |


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
