# Обработать документы

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (180).png>)

![](<../../../../.gitbook/assets/image (391).png>)

Элемент, осуществляющий обработку документов на сервере Dbrain

| Свойство   | Тип                                                                                      | Описание                               |
| ---------- | ---------------------------------------------------------------------------------------- | -------------------------------------- |
| Документ\* | String                                                                                   | Путь к файлу обрабатываемого документа |
| Инвойс     | Boolean                                                                                  | Признак бухгалетрского документа       |
| Результат  | [LTools.OCR.Model.Dbrain. DbrainRecognitionResult](datatypes/dbrainrecognitionresult.md) | Результат обработки документов         |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.DbrainApp app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
LTools.OCR.Model.Dbrain.DbrainRecognitionResult txt = app.ProcessDocs("Файл 1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000)
txt = app.ProcessDocs("Файл 1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
var txt = app.ProcessDocs("Файл 1");
```
{% endtab %}
{% endtabs %}
