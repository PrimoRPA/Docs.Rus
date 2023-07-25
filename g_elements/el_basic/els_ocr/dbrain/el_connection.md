# Сервер Dbrain

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (213).png>)

![](<../../../../.gitbook/assets/image (411).png>)

Элемент, подключающий к серверу Dbrain

| Свойство | Тип                                                                                                                    | Описание                       |
| -------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| Сервер   | String                                                                                                                 | URL сервера                    |
| Токен    | String                                                                                                                 | Токен подключения              |
| Порог    | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0\&viewFallbackFrom=windowsdesktop-3.0) | Порог корректности             |
| Ошибка   | double                                                                                                                 | Порог ошибки                   |
| Тайм-аут | Int32                                                                                                                  | Тайм-аут действий сервера (мс) |

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
