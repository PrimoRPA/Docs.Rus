---
description: Execute query
---

# Выполнить запрос



![](<../../../.gitbook/assets/image (374).png>)

Компонент, выполняющий запрос 1С.

### Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Символ `*` указывает на обязательность заполнения.

| Свойство    | Тип                                      | Описание                             |
| ----------- | ---------------------------------------- | ------------------------------------
| **1С**  |  |
| Запрос\*            | String                | Запрос на языке 1С                            |
| Наличие результатов | Boolean               | Признак ожидания результатов запроса          |
|Не отключаться       |Boolean | Не разрывать соединение с 1C. ***Функция доступна с версии 1.25.1***|
| **Вывод**  |  |
| Переменная\*        | System.Data.DataTable | Переменная для сохранения результатов запроса |


## Только код


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OneSApp app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
System.Data.DataTable data = app.ExecuteQuery("ВЫБРАТЬ * ИЗ", true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password")
data = app.ExecuteQuery("ВЫБРАТЬ * ИЗ", True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OneSApp.Init(wf, _lib.LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
var data = app.ExecuteQuery("ВЫБРАТЬ * ИЗ", true);
```
{% endtab %}
{% endtabs %}
