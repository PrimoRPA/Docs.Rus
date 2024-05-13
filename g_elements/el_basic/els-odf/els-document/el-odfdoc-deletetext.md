---
description: Delete text
---
# Удалить текст
  
![](../../../../.gitbook/assets1/odfdoc-deletetext.png)

Элемент удаляет текст заданной длины. Элемент работает корректно только внутри контейнера "Документ ODF".

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Word**  
1. **Начало** *[Int32]* - Индекс символа начала текста (отсчет ведется с нуля, значение по умолчанию - ноль). Пример: `15`   
1. **Длина** *[Int32]* - Длина текста (по умолчанию - до конца документа). Пример: `14`

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):  
{% tabs %}  
{% tab title="C#" %}  
```csharp  
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");  
app.DeleteText(10, 100);  
```
{% endtab %}  
{% tab title="Python" %}  
```python  
app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName")  
app.DeleteText(10, 100)  
```
{% endtab %}  
{% tab title="JavaScript" %}  
```javascript  
var app =  _lib.Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");  
app.DeleteText(10, 100);  
```
{% endtab %}  
{% endtabs %}  

