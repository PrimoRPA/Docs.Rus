# Выполнить команду сервера

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (3).png>)

![](<../../../../.gitbook/assets/image (303).png>)

Компонент, выполняющий команду на терминальном сервере

| Свойство  | Тип    | Описание                     |
| --------- | ------ | ---------------------------- |
| Команда\* | String | Выполняемая команда          |
| Вывод     | String | Результат выполнения команды |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.TServerApp app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
string ret = app.Execute(command);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000)
ret = app.Execute("cmd")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
var ret = app.Execute("cmd");
```
{% endtab %}
{% endtabs %}
