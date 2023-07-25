# Классифицировать документы

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (115).png>)

![](<../../../../.gitbook/assets/image (344).png>)

Элемент, осуществляющий классификацию документов на сервере Dbrain

| Свойство   | Тип                                                                                            | Описание                               |
| ---------- | ---------------------------------------------------------------------------------------------- | -------------------------------------- |
| Документ\* | String                                                                                         | Путь к файлу обрабатываемого документа |
| Результат  | [LTools.OCR.Model.Dbrain. DbrainClassificationResult](datatypes/dbrainclassificationresult.md) | Результат обработки документов         |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.DbrainApp app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
LTools.OCR.Model.Dbrain.DbrainClassificationResult txt = app.ClassifyDocs("Файл 1");	
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000)
txt = app.ClassifyDocs("Файл 1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.DbrainApp.Init(wf, "server", "token", 10000);
var txt = app.ClassifyDocs("Файл 1");
```
{% endtab %}
{% endtabs %}
