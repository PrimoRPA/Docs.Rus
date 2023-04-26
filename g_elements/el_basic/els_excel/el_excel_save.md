# Сохранить документ

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (196).png>)

![](<../../../.gitbook/assets/image (283).png>)

Элемент сохраняет файл Excel. Корректно работает только внутри контейнера **Приложение Excel**.

Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Excel. 

## Свойства

| Свойство     | Тип    | Описание                                  |
| ------------ | ------ | ----------------------------------------- |
| ***Общие***          | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Excel***          | |  | 
| Путь к файлу | String | Путь к файлу Excel. Пример: `"C:\folder\files.xlsx"`. Доступно сохранение в формате XLSB |

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file2");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.Save()
app.SaveAs("file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file");
```
{% endtab %}
{% endtabs %}
