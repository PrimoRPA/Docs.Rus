# Приложение Outlook

![](<../../../.gitbook/assets/image (190).png>)

Компонент осуществляет подключение к приложению Outlook.

## Свойства
Свойства разделены на группы, название каждой выделено жирным курсивом.

| Свойство    | Тип    | Описание                      |
| ----------- | ------ | ----------------------------- |
| ***Общие***  |  | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Outlook*** |  |  |
| Имя профиля | String | Имя профиля Outlook. Пример: `"Outlook"` |
| Пароль      | String | Пароль профиля Outlook        |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Если используется пароль в зашифрованном виде, укажите его в этом поле. В целях безопасности пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из **Диспетчера учетных данных** (Credential Manager) |
| ***Вывод*** |  |  |
| Переменная  | LTools.Office.OutlookInst | Переменная, которая будет хранить ссылку на установленное подключение  |

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}
{% endtabs %}
