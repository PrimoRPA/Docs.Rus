# Информация о файле

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (247).png>)

![](<../../../../.gitbook/assets/Информация о файле.png>)

Компонент, получающий информацию о файле или папке.

| Свойство             | Тип                                                               | Описание                                           |
| -------------------- | ----------------------------------------------------------------- | -------------------------------------------------- |
| Путь\*               | String                                                            | Путь к читаемому файлу/папке. Например, "c:\folder\file.txt" |
| Переменная           | LTools.Data.Model.FileInfo                                        | Свойство вывода. Переменная, которая будет хранить информацию о файле/папке     |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Data.Model.FileInfo inf = LTools.Data.Model.FileInfo.ReadInfo(@"c:\folder\file.txt");
```
{% endtab %}

{% tab title="Python" %}
```python
inf = LTools.Data.Model.FileInfo.ReadInfo("c:\folder\file.txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var inf = _lib.LTools.Data.Model.FileInfo.ReadInfo("c:\\folder\\file.txt");
```
{% endtab %}
{% endtabs %}
