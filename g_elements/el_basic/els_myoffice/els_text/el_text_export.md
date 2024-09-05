# Экспортировать документ

![](<../../../../.gitbook/assets/image (481).png>)

Элемент производит экспорт текстового документа в другой формат. Путь до исходного файла указывается в контейнере [МойОфис Текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_text/el_text_app).

## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство     | Тип                                    | Описание                           |
| ------------ | -------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                 | Путь к экспортированному файлу (c:\folder\files.pdf) |
| Формат       | LTools.Office.Model. WordExportFormats | Тип формата. В настоящее время доступен только формат `Pdf`|


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.Export(@"c:\folder\files.pdf", [format]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.Export("c:\folder\files.pdf", [format])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Export("c:\\folder\\files.pdf", [format]);
```
{% endtab %}
{% endtabs %}
