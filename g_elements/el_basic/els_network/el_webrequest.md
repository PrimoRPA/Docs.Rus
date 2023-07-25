# Запрос WEB-сервиса

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (178).png>)

![](<../../../.gitbook/assets/image (378).png>)

Компонент, осуществляет вызов веб-сервиса по протоколу HTTP.

Свойства элемента можно редактировать в специальном окне, либо в панели Свойства. Данные, указанные в панели Свойства являются приоритетными. Окно редактирования служит для указания константных данных и не позволяет использовать выражения языка C#. Для вызова окна редактирования нужно нажать кнопку ![](<../../../.gitbook/assets/2 (2).png>)

![](<../../../.gitbook/assets/3 (1).png>)

| Свойство           | Тип                                                                                | Описание                                                  |
| ------------------ | ---------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Переменная запроса | [LTools.Network.Model.TrafficHistoryItem](datatypes/traffichistoryitem.md)         | Переменная, содержащая информацию о производимом запросе  |
| URL                | String                                                                             | URL Web-сервиса                                           |
| Body               | String                                                                             | Тело запроса Web-сервиса                                  |
| Headers            | IEnumerable<[LTools.Network.Model.PackageHeader](datatypes/packageheader.md)>      | Массив заголовков запроса Web-сервиса                     |
| Результат          | [LTools.Network.Model.TrafficEmitterResponse](datatypes/trafficemitterresponse.md) | Переменная для сохранения результатов запроса Web-сервиса |
| Файл               | String                                                                             | Путь сохранения файла                                     |
| Таймаут            | Int32                                                                              | Предельное время ожидания завершения процесса (мс)        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.Model.TrafficHistoryItem req = new LTools.Network.Model.TrafficHistoryItem();
req.URL = "http://api.mathjs.org/v4/";
req.Body = @"
	{
	    ""expr"": [
	      ""a = 1.2 * (2 + 4.5)"",
	      ""a / 2"",
	      ""5.08 cm in inch"",
	      ""sin(45 deg) ^ 2"",
	      ""9 / 3 + 2i"",
	      ""b = [-1, 2; 3, 1]"",
	      ""det(b)""
	    ],
	    ""precision"": 14
	  }";
req.ContentType = "application/json";
req.Headers = new System.Collections.ObjectModel.ObservableCollection<LTools.Network.Model.PackageHeader>() { new LTools.Network.Model.PackageHeader() { Name = "Header1", Value = "hdr" } };
req.Method = "POST";
LTools.Network.Model.TrafficEmitterResponse resp = LTools.Network.NetworkApp.WebRequest(wf, req, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
req = LTools.Network.Model.TrafficHistoryItem();
req.URL = "http://api.mathjs.org/v4/";
req.Body = """
	{
	    ""expr"": [
	      ""a = 1.2 * (2 + 4.5)"",
	      ""a / 2"",
	      ""5.08 cm in inch"",
	      ""sin(45 deg) ^ 2"",
	      ""9 / 3 + 2i"",
	      ""b = [-1, 2; 3, 1]"",
	      ""det(b)""
	    ],
	    ""precision"": 14
	  }""";
req.ContentType = "application/json";
hdr = LTools.Network.Model.PackageHeader();
hdr.Name = "Header1";
hdr.Value = "hdr";
req.Headers = System.Collections.ObjectModel.ObservableCollection[LTools.Network.Model.PackageHeader]();
req.Headers.Add(hdr)
req.Method = "POST";
resp = LTools.Network.NetworkApp.WebRequest(wf, req, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var req = host.newObj(_lib.LTools.Network.Model.TrafficHistoryItem);
req.URL = "http://api.mathjs.org/v4/";
req.Body = `"
	{
	    "expr": [
	      "a = 1.2 * (2 + 4.5)",
	      "a / 2",
	      "5.08 cm in inch",
	      "sin(45 deg) ^ 2",
	      "9 / 3 + 2i",
	      "b = [-1, 2; 3, 1]",
	      "det(b)"
	    ],
	    "precision": 14
	  }"`;
req.ContentType = "application/json";
var hdr = host.newObj(_lib.LTools.Network.Model.PackageHeader);
hdr.Name = "Header1";
hdr.Value = "hdr";
req.Headers = host.newObj(_lib.System.Collections.ObjectModel.ObservableCollection(_lib.LTools.Network.Model.PackageHeader));
req.Headers.Add(hdr)
req.Method = "POST";
var resp = _lib.LTools.Network.NetworkApp.WebRequest(wf, req, 10000);
```
{% endtab %}
{% endtabs %}
