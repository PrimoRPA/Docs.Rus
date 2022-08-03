# Закрыть Outlook

![](<../../../.gitbook/assets/image (166).png>)

Компонент, закрывающий приложение Outlook. Компонент корректно работает только внутри контейнера Приложение Outlook.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
app.Close();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
app.Close();
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
app.Close();
```
{% endtab %}
{% endtabs %}
