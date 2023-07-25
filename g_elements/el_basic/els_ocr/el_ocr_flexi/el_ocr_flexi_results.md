# Результаты обработки

![](../../../.gitbook/assets/image%20\(100\)%20\(1\)%20\(1\)%20\(1\)%20\(2\)%20\(83\).png)

![](../../../.gitbook/assets/%D0%A0%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B%20%D0%BE%D0%B1%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B8.png)

Элемент помогает получить результаты асинхронной обработки документов на сервере FlexiCapture.

Корректно работает внутри контейнера **Сервер FlexiCapture**.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство      | Тип                                                                                 | Описание                                                                                                |
| ------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Пакет\*       | [LTools.OCR.Model.FlexiCapture.BatchInfo](tipy-dannykh/batchinfo.md)                | Информация о пакете                                                                                     |
| Таймаут\*     | Int32                                                                               | Укажите предельное время ожидания завершения процесса (мс)                                              |
| Удалять пакет | Boolean                                                                             | Определяет, нужно ли удалять пакет по завершении обработки. Если флаг установлен, то пакет будет удален |
| Результат     | [LTools.OCR.Model.FlexiCapture.RecognitionResults](datatypes/recognitionresults.md) | Результат обработки документов                                                                          |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.FlexiApp app = LTools.OCR.FlexiApp.Init(wf, "server");
LTools.OCR.Model.FlexiCapture.BatchInfo btch = app.ProcessDocsAsync("project", "batch", new List<string>() { @"c:\file.png" });
LTools.OCR.Model.FlexiCapture.RecognitionResults txt = app.GetProcessResult(btch);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.FlexiApp.Init(wf, "server")
btch = app.ProcessDocsAsync("project", "batch", List[String]([ @"c:\file.png" ]))
txt = app.GetProcessResult(btch);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.FlexiApp.Init(wf, "server");
		var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("c:\\file.png");
var btch = app.ProcessDocsAsync("project", "batch", lst);
var txt = app.GetProcessResult(btch);
```
{% endtab %}
{% endtabs %}
