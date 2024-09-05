# Вставить таблицу

![](<../../../../.gitbook/assets/image (552).png>)

Элемент вставляет таблицу в документ. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Чтобы сохранить изменения в файле, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_save).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип                   | Описание                                                                                      |
| -------- | --------------------- | --------------------------------------------------------------------------------------------- |
| Закладка | String                | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Данные   | List\<List\<String>>  | Данные таблицы                                                                                |
| Таблица  | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0) | Название переменной с табличными данными |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.InsertTable(data, [bookmark]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.InsertTable(data, [bookmark])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.InsertTable(data, [bookmark]);
```
{% endtab %}
{% endtabs %}
