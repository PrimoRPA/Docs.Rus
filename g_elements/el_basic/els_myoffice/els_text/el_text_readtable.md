# Прочитать таблицу

![](<../../../../.gitbook/assets/image (506).png>)

Элемент читает таблицу из текстового документа. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Результат чтения сохраняется в указанную переменную.


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип                   | Описание                 |
| -------- | --------------------- | ------------------------ |
| Индекс\*   | Int32               | Порядковый номер таблицы |
| Данные   | List\<List\<String>>  | Название переменной, в которую будут сохранены двумерный список текстовых данных |
| Таблица  | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0) | Название переменной, в которую будут сохранены табличные данные |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
List<List<string>> list = app.ReadTableArr(1);
System.Data.DataTable table = app.ReadTable(1);
```
{% endtab %}

{% tab title="Python" %}
```python
list = app.ReadTableArr(1) #List<List<string>>
table = app.ReadTable(1) #System.Data.DataTable
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var list = app.ReadTableArr(1); //List<List<string>>
var table = app.ReadTable(1); //System.Data.DataTable
```
{% endtab %}
{% endtabs %}
