# Сохранить документ

![](<../../../.gitbook/assets/image (851).png>)



Компонент, производящий сохранения файла PowerPoint. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера PowerPoint.

Свойства

| Свойство     | Тип    | Описание                                       |
| ------------ | ------ | ---------------------------------------------- |
| Путь к файлу | String | Путь к файлу PowerPoint (c:\folder\files.pptx) |

{% tabs %}
{% tab title="C#" %}
```csharp
app.Save();
app.SaveAs("C:\\file.pptx");
```
{% endtab %}

{% tab title="Python" %}
```python
app.Save()
app.SaveAs("C:\\file.pptx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Save();
app.SaveAs("C:\\file.pptx");
```
{% endtab %}
{% endtabs %}
