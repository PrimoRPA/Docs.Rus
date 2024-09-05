# Сохранить документ

![](<../../../../.gitbook/assets/image (484).png>)

Элемент сохраняет текущее состояние файла таблицы. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Таблицы.

## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство     | Тип    | Описание                                    |
| ------------ | ------ | ------------------------------------------- |
| Путь к файлу | String | Путь к файлу таблицы (c:\folder\files.xlsx) |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.Save();
app.SaveAs(@"c:\folder\files.xls");
```
{% endtab %}

{% tab title="Python" %}
```python
app.Save()
app.SaveAs("c:\folder\files.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.Save();
app.SaveAs("c:\\folder\\files.xls");
```
{% endtab %}
{% endtabs %}
