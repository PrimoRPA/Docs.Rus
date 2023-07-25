# Добавление водяного знака

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (196).png>)

![](<../../../.gitbook/assets/image (331).png>)

Компонент, добавляющий водяной знак к документу PDF

| Свойство            | Тип    | Описание                                |
| ------------------- | ------ | --------------------------------------- |
| Текст\*             | String | Текст водяного знака                    |
| Имя шрифта\*        | String | Имя шрифта водяного знака (Arial Black) |
| Размер шрифта\*     | int    | Размер шрифта водяного знака            |
| Путь к файлу\*      | String | Путь к файлу PDF                        |
| Пароль              | String | Пароль документа PDF                    |
| Путь к результату\* | String | Путь к результирующему файлу PDF        |
| Страницы            | String | Номера страниц документа (1,2,4)        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.PdfApp.AddWatermark(wf, "Файл 1", "Файл назначения", "Текст знака", "пароль", "1,2", "Arial Black", 10);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Office.PdfApp.AddWatermark(wf, "Файл 1", "Файл назначения", "Текст знака", "пароль", "1,2", "Arial Black", 10)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Office.PdfApp.AddWatermark(wf, "Файл 1", "Файл назначения", "Текст знака", "пароль", "1,2", "Arial Black", 10);
```
{% endtab %}
{% endtabs %}
