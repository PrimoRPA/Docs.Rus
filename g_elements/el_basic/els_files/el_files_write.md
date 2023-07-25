# Запись в файл

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (309).png>)

![](<../../../.gitbook/assets/image (14).png>)

Компонент, перезаписывающий содержимое файла.

| Свойство       | Тип     | Описание                                                                                                                                                                       |
| -------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Кодировка      | String  | Кодировка, используемая в файле (utf-8) '[https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding](https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding)' |
| Путь к файлу\* | String  | Путь к файлу для записи (c:\folder\file.txt)                                                                                                                                   |
| Текст          | String  | Текст записываемый в файл                                                                                                                                                      |
| Массив         | byte\[] | Двоичные данные, записываемые в файл                                                                                                                                           |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.File.WriteAllLines(@"C:\text.txt", new List<string>() { "New text" });
System.IO.File.WriteAllText(@"C:\text.txt", "New text");
System.IO.File.WriteAllBytes(@"C:\bytes.txt", new byte[0]);
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.File.WriteAllLines("C:\\text.txt", List[String](["New text"]))
System.IO.File.WriteAllText("C:\\text.txt", "New text")
System.IO.File.WriteAllBytes("C:\\bytes.txt", Array[Byte]([]))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var items = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
items.Add("New text");
_lib.System.IO.File.WriteAllLines("C:\\text.txt", items);
_lib.System.IO.File.WriteAllText("C:\\text.txt", "New text");
var bytes = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Byte));
_lib.System.IO.File.WriteAllBytes("C:\\bytes.txt", bytes.ToArray());
```
{% endtab %}
{% endtabs %}
