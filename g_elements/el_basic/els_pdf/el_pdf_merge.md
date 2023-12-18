# Объединение документов

*Eng: Merge documents*

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (36).png>)

![](<../../../.gitbook/assets/image (445).png>)

Элемент позволяет объединить два документа PDF в один.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство            | Тип    | Описание                         |
| ------------------- | ------ | -------------------------------- |
| Путь к файлу 1\*    | String | Путь к первому файлу PDF         |
| Путь к файлу 2\*    | String | Путь ко второму файлу PDF        |
| Путь к результату\* | String | Путь к результирующему файлу PDF |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Office.PdfApp.Merge(wf, "Файл 1", "Файл 2", "Файл назначения");
```
{% endtab %}
{% endtabs %}
