---
description: Get shapes
---


# Получение фигур

Элемент получает данные фигур из документа Word. Путь до документа указывается в контейнере [**Документ Word**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_word/el_word_app).

![](<../../../.gitbook/assets1/word-get-shapes.png>)

## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

* **Переменная*** *[List<LTools.Office.Model.Word.DocShape>]* - название переменной для хранения результатов чтения.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Инициализировать документ Word
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, @".\Test.docx", LTools.Office.Model.InteropTypes.DX);
		
//Компонент, получающий данные фигур из документа Word. Свойства
//app - [LTools.Office.WordApp] Приложение Word
//List<LTools.Office.Model.Word.DocShape> txt = app.GetShapes();
		
List<LTools.Office.Model.Word.DocShape> txt = app.GetShapes();
		
//Добавить запись в лог
LTools.Workflow.PrimoApp.AddToLog(wf, "Количество найденных фигур: "+ txt.Count, LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
#Компонент, производящий подключение к приложению Word
app = LTools.Office.WordApp.Init(wf, ".\\Test.docx", LTools.Office.Model.InteropTypes.DX)
	
#Компонент, получающий данные фигур из документа Word.  Свойства
#app - [LTools.Office.WordApp] Приложение Word
#txt = app.GetShapes() #List<LTools.Office.Model.Word.DocShape>
txt = app.GetShapes() 
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Компонент, производящий подключение к приложению Word
let app = _lib.LTools.Office.WordApp.Init(wf, ".\Test.docx", _lib.LTools.Office.Model.InteropTypes.DX);

//Компонент, получающий данные фигур из документа Word.  Свойства
//app - [LTools.Office.WordApp] Приложение Word
//let txt = app.GetShapes(); //List<LTools.Office.Model.Word.DocShape>
let txt = app.GetShapes();
```
{% endtab %}
{% endtabs %}

