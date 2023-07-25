# Чтение файла

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (335).png>)

![](<../../../.gitbook/assets/image (96).png>)

Компонент, читающий содержимое файла.

| Свойство                 | Тип                   | Описание                                                                                                                                                                       |
| ------------------------ | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Путь\*                   | String                | Путь к читаемому файлу (c:\folder\file.txt)                                                                                                                                    |
| Переменная (текст)       | String                | Переменная, принимающая текстовые данные файла                                                                                                                                 |
| Переменная (массив)      | byte\[]               | Переменная, принимающая двоичные данные файла                                                                                                                                  |
| Кодировка                | String                | Кодировка, используемая в файле (utf-8) '[https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding](https://docs.microsoft.com/ru-ru/dotnet/api/system.text.encoding)' |
| Переменная (изображение) | System.Drawing.Bitmap | Переменная, принимающая изображение из файла                                                                                                                                   |

{% tabs %}
{% tab title="C#" %}
```csharp
string txt = System.IO.File.ReadAllText(@"C:\text.txt");
byte[] bytes = System.IO.File.ReadAllBytes(@"C:\bytes.txt");
System.Drawing.Bitmap bmp = System.Drawing.Bitmap.FromFile("file");
```
{% endtab %}

{% tab title="Python" %}
```python
txt = System.IO.File.ReadAllText("C:\\text.txt")
bytes = System.IO.File.ReadAllBytes("C:\\bytes.txt")
bmp = System.Drawing.Bitmap.FromFile("file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var txt = _lib.System.IO.File.ReadAllText("C:\\text.txt");
var bytes = _lib.System.IO.File.ReadAllBytes("C:\\bytes.txt");
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var bmp = host.newObj(_lib.System.Drawing.Bitmap, "file");
```
{% endtab %}
{% endtabs %}
