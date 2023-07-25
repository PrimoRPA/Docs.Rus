# Чтение текста

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (41).png>)

![](<../../../.gitbook/assets/image (370).png>)

Компонент, получающий текст документа PDF

| Свойство       | Тип                          | Описание                                   |
| -------------- | ---------------------------- | ------------------------------------------ |
| Путь к файлу\* | String                       | Путь к файлу PDF                           |
| Пароль         | String                       | Пароль документа PDF                       |
| Страницы       | String                       | Номера страниц документа (1,2,4)           |
| Переменная     | List\<System.Drawing.Bitmap> | Переменная для хранения результатов чтения |

{% tabs %}
{% tab title="C#" %}
```csharp
string txt = LTools.Office.PdfApp.ReadText(wf, "Файл 1", "пароль", "1,2");
```
{% endtab %}

{% tab title="Python" %}
```python
txt = LTools.Office.PdfApp.ReadText(wf, "Файл 1", "пароль", "1,2")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var txt = _lib.LTools.Office.PdfApp.ReadText(wf, "Файл 1", "пароль", "1,2");
```
{% endtab %}
{% endtabs %}
