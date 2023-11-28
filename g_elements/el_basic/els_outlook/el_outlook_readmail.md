# Чтение почты

*Eng: Read mail*

Элемент позволяет читать электронные письма в Outlook. В свойствах указываем путь до папки Outlook, которую необходимо прочесть. Список полученных писем робот сохранит в переменную вывода.

Поддерживается чтение только сообщений почты и отчетов о доставке. Если в указанной папке находится письмо с неподдерживаемым типом (например, [контакты, приглашение на собрание](https://learn.microsoft.com/ru-ru/office/vba/outlook/concepts/forms/item-types-and-message-classes)), робот его прочитать не сможет, а обратится к следующим письмам.

Элемент должен располагаться внутри контейнера [Приложение Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_app), которое отвечает за подключение к почтовому клиенту. Не забудьте указать корректные настройки подключения перед тем, как начать работу.

![](<../../../.gitbook/assets/image (109).png>)

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                               | Описание                                         |
| -------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------ |
| ***Outlook:***        |  |  |
| Путь к папке         | String                                                                            | Путь к папке Outlook. Пример: `@"\\user@domen.ru\Inbox"`. Язык указания почтового ящика зависит от языка отображения папок в Outlook  |
| Отчеты               | Boolean                                                                           | Определяет, нужно ли читать отчеты о доставке. Если чекбокс установлен, робот будет читать отчеты  |
| Не читать тело       | Boolean                                                                           | Определяет, требуется ли читать тело письма. При установке чекбокса тело письма **НЕ** будет прочитано |
| Читать свойства      | Boolean                                                                           | Определяет, нужно ли читать свойства писем. Прочитанные свойства можно просмотреть в модели письма **OMailMessage** в поле `MessageProperties`. <p>Пример обращения к свойствам письма: `<variable name>[0].MessageProperties`, где **\<variable name>** - название переменной вывода, хранящей список прочитанных писем, а [0] - индекс письма <p/>|
| Только непрочитанные | Boolean                                                                           | Определяет, следует ли читать только непрочитанные письма. По умолчанию чекбокс снят - читаются все письма |
| Запрос               | String                                                                            | Поле для указания поискового запроса писем. Запросы основаны на поиске по ключевым словам. Пример: `@SQL="urn:schemas:httpmail:subject" like '%Office%'` |
| ***Вывод:***         |  |  |
| Переменная\*         | List <[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)> | Переменная для сохранения списка полученных писем. Отсчет сообщений в списке производится с 0 |


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

