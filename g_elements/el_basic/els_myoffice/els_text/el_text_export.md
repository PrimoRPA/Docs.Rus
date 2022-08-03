# Экспортировать документ

![](<../../../../.gitbook/assets/image (481).png>)

Компонент, производящий экспорт документа Текст в другой формат.

| Свойство     | Тип                                    | Описание                           |
| ------------ | -------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                 | Путь к файлу (c:\folder\files.pdf) |
| Формат       | LTools.Office.Model. WordExportFormats | Тип формата                        |

{% tabs %}
{% tab title="C#" %}
```csharp
app.Export(@"c:\folder\files.pdf", [format]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.Export("c:\folder\files.pdf", [format])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Export("c:\\folder\\files.pdf", [format]);
```
{% endtab %}
{% endtabs %}
