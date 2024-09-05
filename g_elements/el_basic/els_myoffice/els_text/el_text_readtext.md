# Чтение текста

![](<../../../../.gitbook/assets/image (807).png>)

Элемент считывает данные из текстового документа. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Результат чтения сохраняется в указанную переменную.

## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство   | Тип    | Описание                                   |
| ---------- | ------ | ------------------------------------------ |
| Переменная | String | Переменная для хранения результатов чтения |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
string txt = app.ReadText();
```
{% endtab %}

{% tab title="Python" %}
```python
txt = app.ReadText() #String
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let txt = app.ReadText(); //String
```
{% endtab %}
{% endtabs %}
