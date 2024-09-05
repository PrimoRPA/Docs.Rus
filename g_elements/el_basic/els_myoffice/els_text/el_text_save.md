# Сохранить документ

![](<../../../../.gitbook/assets/image (545).png>)

Элемент сохраняет текущее состояние текстового файла. Путь к исходному файлу указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

Если в свойствах элемента **Сохранить документ** не указывать путь к файлу, то сохранится файл, который был открыт в рамках контейнера **МойОфис Текст**.


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип    | Описание                                  |
| ------------ | ------ | ----------------------------------------- |
| Путь к файлу | String | Путь к файлу Текст (c:\folder\files.docx) |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.Save();
app.SaveAs(@"c:\folder\files.docx");
```
{% endtab %}

{% tab title="Python" %}
```python
app.Save()
app.SaveAs("c:\folder\files.docx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Save();
app.SaveAs("c:\\folder\\files.docx");
```
{% endtab %}
{% endtabs %}
