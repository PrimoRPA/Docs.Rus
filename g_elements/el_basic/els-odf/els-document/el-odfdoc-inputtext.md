# Ввод текста

![](<../../../../.gitbook/assets1/Cropped-InputText.png>)

Компонент, производящий запись данных в документ Word. 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Закладка** *[String]*: Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста 
2. **Начало** *[Int32]*: Индекс начала вставки                                                                         
3. **Текст\*** *[String]* Данные, вводимые в документ                                                                   

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`  
`app.AppendText(text, [selStart]);`  
`app.AppendText(text, bookmark);`
