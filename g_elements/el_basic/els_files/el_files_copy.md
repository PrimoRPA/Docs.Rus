# Копировать файл

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (229).png>)

![](<../../../.gitbook/assets/image (45).png>)

Компонент, копирующий файл.

| Свойство     | Тип     | Описание                                      |
| ------------ | ------- | --------------------------------------------- |
| Источник\*   | String  | Путь к файлу-источнику (c:\folder\file1.txt)  |
| Назначение\* | String  | Путь к файлу назначения (c:\folder\file2.txt) |
| Перезаписать | Boolean | Признак перезаписи файла назначения           |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.File.Copy(@"C:\from", @"C:\to");
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.File.Copy("C:\\from", "C:\\to")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.System.IO.File.Copy("C:\\from", "C:\\to");
```
{% endtab %}
{% endtabs %}
