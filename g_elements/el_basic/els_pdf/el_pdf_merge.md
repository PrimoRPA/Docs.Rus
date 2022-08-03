# Объединение документов

![](<../../../.gitbook/assets/image (542).png>)

![](<../../../.gitbook/assets/image (120).png>)

Компонент, получающий кол-во страниц документа PDF

| Свойство            | Тип    | Описание                         |
| ------------------- | ------ | -------------------------------- |
| Путь к файлу 1\*    | String | Путь к первому файлу PDF         |
| Путь к файлу 2\*    | String | Путь ко второму файлу PDF        |
| Путь к результату\* | String | Путь к результирующему файлу PDF |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения");
```
{% endtab %}
{% endtabs %}
