# Сервер Dbrain

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (33).png>)

![](<../../../../.gitbook/assets/image (411).png>)

Элемент, подключающий к серверу Dbrain

| Свойство | Тип    | Описание                       |
| -------- | ------ | ------------------------------ |
| Сервер   | String | URL сервера                    |
| Токен    | String | Токен подключения              |
| Порог    | double | Порог корректности             |
| Ошибка   | double | Порог ошибки                   |
| Тайм-аут | Int32  | Тайм-аут действий сервера (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.DbrainApp app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
```
{% endtab %}
{% endtabs %}
