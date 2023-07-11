# Чтение почты

![](<../../../.gitbook/assets/image (109).png>)

Компонент читает электронные письма из Outlook. Корректно работает только внутри контейнера [Приложение Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_app).

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                               | Описание                                         |
| -------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------ |
| ***Outlook:***        |  |  |
| Путь к папке         | String                                                                            | Путь к папке Outlook. Пример: `"\\user@domen.ru\\Inbox"`  |
| Отчеты               | Boolean                                                                           | Установите отметку, если нужно читать отчеты о доставке |
| Не читать тело       | Boolean                                                                           | Установите отметку, если НЕ требуется читать тело письма |
| Читать свойства      | Boolean                                                                           | Установите отметку, чтобы читать свойства писем |
| Только непрочитанные | Boolean                                                                           | Установите отметку, чтобы получать только непрочитанные сообщения |
| Запрос               | String                                                                            | Поле для указания поискового запроса (`@SQL="urn:schemas:httpmail:subject" like '%Office%'`) |
| ***Вывод:***          |  |  |
| Переменная\*         | List <[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)> | Переменная для сохранения списка писем     |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
List<LTools.Office.Model.OMailMessage> ret = app.ReadMail("\\имя_профиля\Inbox", true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
ret = app.ReadMail("\\имя_профиля\Inbox", True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var ret = app.ReadMail("\\имя_профиля\Inbox", true);
```
{% endtab %}
{% endtabs %}

