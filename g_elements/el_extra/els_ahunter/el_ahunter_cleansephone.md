# Стандартизация телефона

![](<../../../.gitbook/assets/image (878).png>)



Компонент, производящий стандартизацию телефона.

Свойства

| Свойство  | Тип                                          | Описание                         |
| --------- | -------------------------------------------- | -------------------------------- |
| Токен     | String                                       | Токен API                        |
| Телефон   | String                                       | Стандартизируемый телефон        |
| Лимит     | int?                                         | Лимит телефонов                  |
| Тайм-аут  | int                                          | Тайм-аут сервера                 |
| Результат | Primo.AHunter.Model. StPhone.StandartedPhone | Очищенный телефон                |
| Json      | String                                       | Очищенный телефон в формате JSON |

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.AHunter.AHunterApp ah = new Primo.AHunter.AHunterApp();
string a = ah.StandartizePhone("token", "111-22-33", 10, 10000);
Primo.AHunter.Model.StPhone.StandartedPhone sa = ah.ParseStandartPhone(a);
```
{% endtab %}

{% tab title="Python" %}
```python
ah = Primo.AHunter.AHunterApp()
a = ah.StandartizePhone("token", "111-22-33", 10, 10000) #string
sa = ah.ParseStandartPhone(a) #Primo.AHunter.Model.StPhone.StandartedPhone
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
var ah = host.newObj(_lib.Primo.AHunter.AHunterApp);
var a = ah.StandartizePhone("token", "111-22-33", 10, 10000); //string
sa = ah.ParseStandartPhone(a); //_lib.Primo.AHunter.Model.StPhone.StandartedPhone
```
{% endtab %}
{% endtabs %}
