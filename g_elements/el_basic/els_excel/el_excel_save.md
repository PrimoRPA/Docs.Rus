# Сохранить документ

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (196).png>)

![](<../../../.gitbook/assets/image (283).png>)

Элемент сохраняет текущее состояние файла Excel. 

Поддерживаемые расширения:
* XLS;
* XLSM;
* XLSB;
* CVS.

:small_blue_diamond: **Примечание**. Когда вы сохраняете файл в другом формате, часть форматирования, данных и функций может быть потеряна.


### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство     | Тип    | Описание                                  |
| ------------ | ------ | ----------------------------------------- |
| ***Excel***  | |  | 
| Путь к файлу | String | Путь к файлу Excel. Пример: `"C:\folder\files.xlsx"`. <p>Если путь к файлу не указан, сохранится документ, открытый в рамках текущего контейнера Excel </p>|

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
