# Запустить макрос

![](<../../../../.gitbook/assets/image (810).png>)

Элемент выполняет макрос таблицы. Путь к файлу таблицы указывается в контейнере [МойОфис Таблица](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_app).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип    | Описание                     |
| ------------ | ------ | ---------------------------- |
| Наименование | String | Наименование макроса         |
| Переменная   | Object | Название переменной, в которую будет сохранен результат выполнения скрипта |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.RunMacro("MacroName");
```
{% endtab %}

{% tab title="Python" %}
```python
app.RunMacro("MacroName")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.RunMacro("MacroName");
```
{% endtab %}
{% endtabs %}

