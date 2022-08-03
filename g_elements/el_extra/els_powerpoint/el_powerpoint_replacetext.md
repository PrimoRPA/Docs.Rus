# Заменить текст

![](<../../../.gitbook/assets/image (572).png>)



Компонент, производящий замену текста в презентации.

Свойства

| Свойство         | Тип     | Описание                      |
| ---------------- | ------- | ----------------------------- |
| Исходный текст   | String  | Исходный текст                |
| Замена           | String  | Текст на замену               |
| Заменить все     | Boolean | Заменить все вхождения текста |
| Слова целиком    | Boolean | Заменять только слова целиком |
| Регистр          | Boolean | Учитывать регистр             |
| Кол-во изменений | Int32   | Кол-во изменений              |

{% tabs %}
{% tab title="C#" %}
```csharp
int cnt = app.AddFile("old text", "new text", true, true, false);
```
{% endtab %}

{% tab title="Python" %}
```python
cnt = app.AddFile("old text", "new text", True, True, False) #int
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var cnt = app.AddFile("old text", "new text", true, true, false); //int
```
{% endtab %}
{% endtabs %}
