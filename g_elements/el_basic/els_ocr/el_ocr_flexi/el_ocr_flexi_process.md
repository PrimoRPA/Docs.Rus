# Обработать документы

![](<../../../../.gitbook/assets/image (31).png>)

Элемент, осуществляющий обработку документов на сервере FlexiCapture

| Свойство         | Тип                                                                                     | Описание                                           |
| ---------------- | --------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Проект\*         | String                                                                                  | Имя проекта                                        |
| Пакет\*          | String                                                                                  | Имя пакета                                         |
| Документ         | String                                                                                  | Путь к файлу обрабатываемого документа             |
| Пакет документов | List                                                                                    | Массив путей к файлам документов                   |
| Удалять пакет    | bool                                                                                    | Удалять пакет по завершении обработки              |
| Таймаут\*        | Int32                                                                                   | Предельное время ожидания завершения процесса (мс) |
| Результат        | [LTools.OCR.Model.FlexiCapture. RecognitionResults](tipy-dannykh/recognitionresults.md) | Результат обработки документов                     |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.FlexiApp app = LTools.OCR.FlexiApp.Init(wf, "server");
LTools.OCR.Model.FLexiCapture.RecognitionResults txt = app.ProcessDocs("Проект Flexi", "Имя пакета", new List<string>() { "Файл 1", "Файл 2" }, true, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.FlexiApp.Init(wf, "server");
txt = app.ProcessDocs("Проект Flexi", "Имя пакета", List[String]([ "Файл 1", "Файл 2" ]), True, 10000);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
	
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("Файл 1");
lst.Add("Файл 2");
var app = _lib.LTools.OCR.FlexiApp.Init(wf, "server");
var txt = app.ProcessDocs("Проект Flexi", "Имя пакета", lst, true, 10000);
```
{% endtab %}
{% endtabs %}
