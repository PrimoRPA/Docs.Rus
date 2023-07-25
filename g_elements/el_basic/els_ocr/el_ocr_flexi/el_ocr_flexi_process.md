# Обработать документы

![](<../../../../.gitbook/assets/image (431).png>)

Элемент, осуществляющий обработку (распознавание) документов на сервере FlexiCapture.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство             | Тип                                                                                  | Описание                                                                                  |
| -------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| _**Обработка**_      |                                                                                      |                                                                                           |
| Проект\*             | String                                                                               | Имя проекта                                                                               |
| Пакет\*              | String                                                                               | Имя пакета. По умолчанию - "Primo"                                                        |
| Документ             | String                                                                               | Путь к файлу обрабатываемого документа                                                    |
| Пакет документов     | List\<string>                                                                        | Массив путей к файлам документов                                                          |
| Асинхронный          | bool                                                                                 | Признак асинхронной обработки документов                                                  |
| Игнорировать размер  | bool                                                                                 | Определяет, нужно ли игнорировать размеры файлов                                          |
| Имя файла результата | String                                                                               | Имя файла результата на сервере                                                           |
| Использовать User ID | bool                                                                                 | Определяет, нужно ли использовать User ID. По умолчанию флаг установлен - ID используется |
| Удалять пакет        | bool                                                                                 | Определяет, нужно ли удалять пакет по завершении обработки                                |
| Свойства             | List\<Dictionary\<string, string>>                                                   | Свойства документа                                                                        |
| Таймаут\*            | Int32                                                                                | Предельное время ожидания завершения процесса (мс)                                        |
| _**Вывод**_          |                                                                                      |                                                                                           |
| Пакет                | [LTools.OCR.Model.FlexiCapture.BatchInfo](tipy-dannykh/batchinfo.md)                 | Информация о пакете                                                                       |
| Результат            | [LTools.OCR.Model.FlexiCapture. RecognitionResults](datatypes/recognitionresults.md) | Укажите переменную для сохранения результата обработки документов                         |

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
