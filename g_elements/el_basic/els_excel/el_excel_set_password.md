# Установить пароль

*Eng: Set password*

![](<../../../.gitbook/assets1/setpassw.png>)

Элемент устанавливает пароль для указанного файла Excel. Элемент работает корректно только внутри контейнера **Excel**.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство   | Тип   | Описание                             |
| ---------- | ----- | ------------------------------------ |
| **Пароль\***|*[String]*| Пароль для установки на файл Excel. Пример: `Sbm1kfd0`|


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
app.SetPassword("testpass");
app.Save();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.InitLTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
app.SetPassword("testpass")
app.Save()
```
{% endtab %}


{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SetPassword("testpass");
app.Save();
```
{% endtab %}
{% endtabs %}
