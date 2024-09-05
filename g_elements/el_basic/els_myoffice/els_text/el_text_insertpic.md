# Вставка изображения

![](<../../../../.gitbook/assets/image (559).png>)

Элемент вставляет изображения в текстовый документ. Путь к файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Чтобы сохранить изменения в файле, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_save).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство    | Тип     | Описание                                                                                      |
| ----------- | ------- | --------------------------------------------------------------------------------------------- |
| Изображение\* | byte\[] | Изображение, которое нужно вставить в документ                                              |
| Ширина\*      | float   | Ширина изображения. По умолчанию `100`                                                        |
| Высота\*      | float   | Высота изображения. По умолчанию `100`                                                       |
| Закладка    | String  | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.InsertPicture(pic, "bookmark", 200, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
app.InsertPicture(pic, "bookmark", 200, 100)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.InsertPicture(pic, "bookmark", 200, 100);
```
{% endtab %}
{% endtabs %}
