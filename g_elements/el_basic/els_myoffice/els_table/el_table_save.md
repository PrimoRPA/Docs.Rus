# Сохранить документ

![](<../../../../.gitbook/assets/image (484).png>)

Компонент, производящий сохранения файла Таблицы. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Таблицы.

| Свойство     | Тип    | Описание                                    |
| ------------ | ------ | ------------------------------------------- |
| Путь к файлу | String | Путь к файлу Таблицы (c:\folder\files.xlsx) |

{% tabs %}
{% tab title="C#" %}
```csharp
app.Save();
app.SaveAs(@"c:\folder\files.xls");
```
{% endtab %}

{% tab title="Python" %}
```python
app.Save()
app.SaveAs("c:\folder\files.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Save();
app.SaveAs("c:\\folder\\files.xls");
```
{% endtab %}
{% endtabs %}
