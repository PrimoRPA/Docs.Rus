# Чтение почты

![](<../../../.gitbook/assets/image (109).png>)

Компонент читает электронные письма из Outlook. Корректно работает только внутри контейнера [Приложение Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_app).

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                               | Описание                                         |
| -------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------ |
| ***Outlook:***        |  |  |
| Путь к папке         | String                                                                            | Путь к папке Outlook. Пример: `@"\\user@domen.ru\Inbox"`. Язык указания почтового ящика зависит от языка отображения папок в Outlook  |
| Отчеты               | Boolean                                                                           | Определяет, нужно ли читать отчеты о доставке |
| Не читать тело       | Boolean                                                                           | Определяет, требуется ли читать тело письма. При установке отметки - тело письма НЕ будет прочитано |
| Читать свойства      | Boolean                                                                           | Определяет, нужно ли читать свойства писем. Прочитанные свойства станут доступны в модели письма OMailMessage в поле `.MessageProperties`. Пример обращения к свойствам письма: `var_list_mails[0].MessageProperties`, где var_list_mails - это пример наименования переменной вывода, хранящей список прочитанных писем |
| Только непрочитанные | Boolean                                                                           | Определяет, нужно ли читать только непрочитанные сообщения |
| Запрос               | String                                                                            | Поле для указания поискового запроса писем (`@SQL="urn:schemas:httpmail:subject" like '%Office%'`) |
| ***Вывод:***          |  |  |
| Переменная\*         | List <[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)> | Переменная для сохранения списка полученных писем. Отсчет сообщений в списке производится с 0 |


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

