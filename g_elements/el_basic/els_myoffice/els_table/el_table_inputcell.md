# Ввод в ячейку

![](<../../../../.gitbook/assets/image (503).png>)

Элемент производит запись данных в ячейку таблицы. Путь к файлу таблицы указывается в контейнере [МойОфис Таблица](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_app).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип     | Описание                      |
| --------------- | ------- | ----------------------------- |
| Страница        | String  | Наименование страницы         |
| Индекс страницы | Int32   | Индекс страницы               |
| Как текст       | Boolean | Вставлять значение, как текст |
| Числовой формат | String  | Формат вводимого числа (#,#)  |
| Данные          | String  | Данные, вводимые в ячейку     |
| Ячейка          | String  | Идентификатор ячейки (A4)     |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}
{% endtabs %}
