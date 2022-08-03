# Запись диапазона

![](<../../../.gitbook/assets/image (429).png>)

Компонент, записывающий данные диапазона ячеек в Google Sheets.

| Свойство           | Тип                  | Описание                                       |
| ------------------ | -------------------- | ---------------------------------------------- |
| Диапазон\*         | String               | Диапазон записи ячеек (A1:D12)                 |
| Страница           | String               | Наименование страницы                          |
| Переменная (текст) | List\<List\<object>> | Переменная для хранения данных записи значений |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.GoogleSheetsApp app = LTools.Office.GoogleSheetsApp.Init(wf, @"Путь к файлу токена", @"ID документа");
app.WriteRange(new List<List<object>>() { new List<object>() { "aaa1", "bbb1" } }, "A1:B1", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.GoogleSheetsApp.Init(wf, "C:\\Work\\Primo Test Projects\\ttt\\gstoken\\Google.Apis.Auth.OAuth2.Responses.TokenResponse-user", "11QELuPkG1eD5u3Sn-JSQe4PtJqMqK_-yXKhXiuWQSLA") #LTools.Office.GoogleSheetsApp
app.WriteRange(List[List[object]](), "A1:B1", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
let data = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.Object)));

let app = _lib.LTools.Office.GoogleSheetsApp.Init(wf, "Путь к файлу токена", "ID документа");
app.WriteRange(data, "A1:B1", "Лист1");
```
{% endtab %}
{% endtabs %}

