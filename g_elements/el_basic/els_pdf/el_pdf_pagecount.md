# Кол-во страниц

*Eng: Page count*

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (133).png>)

![](<../../../.gitbook/assets/image (348).png>)

Элемент позволяет получить количество страниц PDF-документа.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                   |
| -------------- | ------ | ------------------------------------------ |
| Путь к файлу\* | String | Путь к файлу PDF                           |
| Пароль         | String | Пароль документа PDF                       |
| Защищенный пароль | SecureString | Защищенный пароль PDF-документа. В целях безопасности пароль в формате SecureString не хранится в открытом виде. Получить его можно, например, из «Диспетчера учетных данных» (Credential Manager) |
| Переменная     | String | Переменная для хранения результатов чтения |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
