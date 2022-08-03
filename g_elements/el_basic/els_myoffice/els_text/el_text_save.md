# Сохранить документ

![](<../../../../.gitbook/assets/image (545).png>)

Компонент, производящий сохранения файла Текст. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Текст.

| Свойство     | Тип    | Описание                                  |
| ------------ | ------ | ----------------------------------------- |
| Путь к файлу | String | Путь к файлу Текст (c:\folder\files.docx) |

{% tabs %}
{% tab title="C#" %}
```csharp
app.Save();
app.SaveAs(@"c:\folder\files.docx");
```
{% endtab %}

{% tab title="Python" %}
```python
app.Save()
app.SaveAs("c:\folder\files.docx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Save();
app.SaveAs("c:\\folder\\files.docx");
```
{% endtab %}
{% endtabs %}
