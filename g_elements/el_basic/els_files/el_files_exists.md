# Существует файл/папка

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (227).png>)

![](<../../../.gitbook/assets/image (189).png>)

Компонент, проверяющий наличие файла либо папки.

| Свойство     | Тип     | Описание                                         |
| ------------ | ------- | ------------------------------------------------ |
| Путь\*       | String  | Путь к проверяемой сущности (c:\folder\file.txt) |
| Переменная\* | Boolean | Переменная - приемник результата проверки        |
| Искать папку | Boolean | Признак поиска папки                             |

{% tabs %}
{% tab title="C#" %}
```csharp
bool f = System.IO.File.Exists(@"C:\text.txt");
bool d = System.IO.Directory.Exists(@"C:\Dir");
```
{% endtab %}

{% tab title="Python" %}
```python
f = System.IO.File.Exists("C:\\text.txt")
d = System.IO.Directory.Exists("C:\\Dir")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var f = _lib.System.IO.File.Exists("C:\\text.txt");
var d = _lib.System.IO.Directory.Exists("C:\\Dir");
```
{% endtab %}
{% endtabs %}
