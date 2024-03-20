# Вставить таблицу

![](<../../../../.gitbook/assets1/Cropped-InsertTable.png>)

Элемент, читающий таблицу из документа. Элемент работает корректно только внутри контейнера.

## Свойства

1. **Закладка** *[String]*: Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста.
2. **Данные** *[List<List<string>>]* Данные таблицы.
3. **Таблица** *[System.Data.DataTable]* Данные таблицы.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`  
`app.InsertTable(data, [bookmark]);`
