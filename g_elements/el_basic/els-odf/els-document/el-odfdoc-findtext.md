# Найти текст

![](<../../../../.gitbook/assets1/Cropped-FindText.png>)

Ищет вхождение заданного текста в документ.

## Свойства

1. **Текст** *[String]*: Искомый текст
2. **Переменная** *[Int32]*: Переменная для хранения индекса первого вхождения текста
3. **Переменная (массив)** *[List\<Int32>]*: Переменная для хранения массива индексов вхождения текста.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`  
`List<int> idxs = app.FindText(text);`  
`int? idx = app.FindTextFirst(text);`
