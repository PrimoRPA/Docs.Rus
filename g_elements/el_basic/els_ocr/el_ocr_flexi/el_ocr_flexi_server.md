# Сервер FlexiCapture

![](<../../../../.gitbook/assets/image (399).png>)

Элемент служит для подключения к серверу FlexiCapture.

| Свойство               | Тип    | Описание                            |
| ---------------------- | ------ | ----------------------------------- |
| Сервер                 | String | URL адрес сервера                   |
| Аутентификация Windows | bool   | Определяет, нужно ли использовать аутентификацию Windows |
| Логин                  | String | Логин пользователя                  |
| Пароль                 | String | Пароль пользователя                 |

{% tabs %}
{% tab title="C#" %}
```csharp
//Аутентификация Windows
LTools.OCR.FlexiApp app = LTools.OCR.FlexiApp.Init(wf, "server");
//Аутентификация логин-пароль
LTools.OCR.FlexiApp app = LTools.OCR.FlexiApp.Init(wf, "server", "login", "pass");
```
{% endtab %}

{% tab title="Python" %}
```python
#Аутентификация Windows
app = LTools.OCR.FlexiApp.Init(wf, "server");
#Аутентификация логин-пароль
app = LTools.OCR.FlexiApp.Init(wf, "server", "login", "pass");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Аутентификация Windows
var app = _lib.LTools.OCR.FlexiApp.Init(wf, "server");
//Аутентификация логин-пароль
var app = _lib.LTools.OCR.FlexiApp.Init(wf, "server", "login", "pass");
```
{% endtab %}
{% endtabs %}
