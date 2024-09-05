# Ввод текста

![](<../../../../.gitbook/assets/image (579).png>)

Элемент записывает данные в текстовый документ. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Чтобы сохранить изменения в файле, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_save).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип    | Описание                                                                                      |
| -------- | ------ | --------------------------------------------------------------------------------------------- |
| Текст\*  | String | Данные, которые будут записаны в документ                                                     |
| Закладка | String | Имя закладки, определяющей начало записи.  Если не указано, позиция записи определяется свойством *Позиция ввода* |
| Позиция ввода | - | Ввод текста в начало/конец. По умолчанию установлено значение `End` |



## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.AppendText("text", bookmark);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AppendText("text", bookmark)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AppendText("text", bookmark);
```
{% endtab %}
{% endtabs %}
