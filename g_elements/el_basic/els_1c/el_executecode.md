# Выполнить код

![](<../../../.gitbook/assets/image (20).png>)



Компонент, выполняющий код 1С.

| Свойство            | Тип     | Описание                                   |
| ------------------- | ------- | ------------------------------------------ |
| Код (выражение)     | String  | Выражение, возвращающее код на языке 1С    |
| Код                 |         | Код на языке 1С                            |
| Наличие результатов | Boolean | Признак ожидания результатов запроса       |
| Переменная          | Object  | Переменная для сохранения результатов кода |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OneSApp app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
object data = app.ExecuteCode("ТекущаяДата();", true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password")
data = app.ExecuteCode("ТекущаяДата();", True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
var data = app.ExecuteCode("ТекущаяДата();", true);
```
{% endtab %}
{% endtabs %}
