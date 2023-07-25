# Добавить строку

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (292).png>)

![](<../../../.gitbook/assets/image (61).png>)

Компонент, добавляющий строку в конец файла.

| Свойство       | Тип    | Описание                                                                                                                                                                       |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Кодировка      | String | Кодировка, используемая в файле (utf-8) '[https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding](https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding)' |
| Путь к файлу\* | String | Путь к файлу для записи (c:\folder\file.txt)                                                                                                                                   |
| Текст\*        | String | Текст записываемой строки                                                                                                                                                      |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.File.AppendAllLines(@"C:\text.txt", new List<string>() { "New text" });
System.IO.File.AppendAllText(@"C:\text.txt", "New text");
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.File.AppendAllLines("C:\\text.txt", List[String](["New text"]))
System.IO.File.AppendAllText("C:\\text.txt", "New text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var items = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
items.Add("New text");
_lib.System.IO.File.AppendAllLines("C:\\text.txt", items);
_lib.System.IO.File.AppendAllText("C:\\text.txt", "New text");
```
{% endtab %}
{% endtabs %}
