# Кол-во страниц

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (2) (54).png>)

![](<../../../.gitbook/assets/image (348).png>)

Компонент, получающий кол-во страниц документа PDF

| Свойство       | Тип    | Описание                                   |
| -------------- | ------ | ------------------------------------------ |
| Путь к файлу\* | String | Путь к файлу PDF                           |
| Пароль         | String | Пароль документа PDF                       |
| Переменная     | String | Переменная для хранения результатов чтения |

{% tabs %}
{% tab title="C#" %}
```csharp
int cnt = LTools.Office.PdfApp.PageCount(wf, "Файл 1", "пароль");
```
{% endtab %}

{% tab title="Python" %}
```python
cnt = LTools.Office.PdfApp.PageCount(wf, "Файл 1", "пароль")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var cnt = _lib.LTools.Office.PdfApp.PageCount(wf, "Файл 1", "пароль");
```
{% endtab %}
{% endtabs %}
