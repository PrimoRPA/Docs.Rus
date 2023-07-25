# Создать папку

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (11).png>)

![](<../../../.gitbook/assets/image (203).png>)

Компонент, создающий новую папку.

| Свойство | Тип    | Описание                             |
| -------- | ------ | ------------------------------------ |
| Путь\*   | String | Путь к создаваемой папке (c:\folder) |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.Directory.CreateDirectory(@"C:\Dir");
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.Directory.CreateDirectory("C:\\Dir")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.System.IO.Directory.CreateDirectory("C:\\Dir");
```
{% endtab %}
{% endtabs %}
