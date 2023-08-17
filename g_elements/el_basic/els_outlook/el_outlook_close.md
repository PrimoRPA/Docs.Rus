# Закрыть Outlook

![](<../../../.gitbook/assets/image (166).png>)

Элемент закрывает приложение Outlook. Корректно работает только внутри контейнера [Приложение Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_app).

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
