# Добавить страницу

![](<../../../../../.gitbook/assets/image (531).png>)

Элемент создает новую страницу в таблице. Путь к файлу таблицы указывается в контейнере [МойОфис Таблица](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_app).

Чтобы сохранить изменения в файле, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_save).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип    | Описание        |
| -------- | ------ | --------------- |
| Имя      | String | Имя страницы    |
| Индекс   | Int32  | Индекс страницы |
| Строки   | Int32  | Кол-во строк    |
| Колонки  | Int32  | Кол-во колонок  |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.SheetAdd("Page1", 20, 3, [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.SheetAdd("Page1", 20, 3, [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SheetAdd("Page1", 20, 3, [sheetIdx]);
```
{% endtab %}
{% endtabs %}
