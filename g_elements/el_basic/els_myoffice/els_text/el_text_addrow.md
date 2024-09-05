# Добавить строку таблицы

![](<../../../../.gitbook/assets/image (474).png>)

Элемент добавляет строку к таблице. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Чтобы сохранить изменения в файле, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_save).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство | Тип                 | Описание                 |
| -------- | ------------------- | ------------------------ |
| Индекс   | Int32               | Порядковый номер таблицы |
| Данные   | List\<String>       | Данные строки            |
| Строка   | System.Data.DataRow | Данные строки            |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddTableRow(1, data);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddTableRow(1, data)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddTableRow(1, data);
```
{% endtab %}
{% endtabs %}
