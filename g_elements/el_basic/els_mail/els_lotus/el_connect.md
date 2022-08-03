# Присоединиться к Lotus Notes

![](<../../../../.gitbook/assets/image (332).png>)

Компонент, осуществляющий подключение к Lotus Notes.

| Свойство   | Тип                                  | Описание                                           |
| ---------- | ------------------------------------ | -------------------------------------------------- |
| Сервер     | String                               | Имя сервера Lotus                                  |
| Файл БД    | String                               | Имя файла БД                                       |
| Пароль     | String                               | Пароль                                             |
| Таймаут\*  | Int32                                | Предельное время ожидания завершения процесса (мс) |
| Переменная | LTools.Network.Model.EMail.LotusInst | Переменная для хранения подключения                |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.LotusApp app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
```
{% endtab %}
{% endtabs %}

