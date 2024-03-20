# Сохранить документ

![](<../../../../.gitbook/assets1/Cropped-SaveDocument.png>)

Компонент, производящий сохранения файла Word. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Word. 

## Свойства

1. **Путь к файлу** *[String]*: Путь к файлу Word (c:\folder\files.docx).

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`  
`app.Save();`  
`app.SaveAs(fileName);`
