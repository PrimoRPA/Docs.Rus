# Чтение текста

![](<../../../../.gitbook/assets1/Cropped-ReadText.png>)

Компонент, считывающий данные из документа Word. 

## Свойство

1. **Переменная** *[String]*: Переменная для хранения результатов чтения.
2. **Начало** *[Int32]*: Начало выделения.
3. **Длина** *[Int32]*: Длина выделения.   

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`   
`string txt = app.ReadText([selStart], [selLength]);`
