# Список страниц

![](<../../../../../.gitbook/assets/image (582).png>)

Элемент получает список страниц таблицы. Путь к файлу таблицы указывается в контейнере [МойОфис Таблица](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_app).

Результат чтения сохраняется в переменную.


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство   | Тип           | Описание                               |
| ---------- | ------------- | -------------------------------------- |
| Переменная | List\<String> | Переменная для хранения списка страниц |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
List<string> sheets = app.GetSheets();
```
{% endtab %}

{% tab title="Python" %}
```python
sheets = app.GetSheets() #List<string>
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let sheets = app.GetSheets(); //List<string>
```
{% endtab %}
{% endtabs %}
