# Получить из буфера обмена

![](<../../../.gitbook/assets/image (367).png>)

Компонент, получающий данные из буфера обмена

| Свойство  | Тип    | Описание          |
| --------- | ------ | ----------------- |
| Результат | Object | Получаемые данные |

{% tabs %}
{% tab title="C#" %}
```csharp
object obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var obj = _lib.LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}
{% endtabs %}

