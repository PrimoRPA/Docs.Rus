# Стандартизация адреса

![](<../../../.gitbook/assets/image (527).png>)



Компонент, производящий стандартизацию адреса.

Свойства

|           |                                                   |                                |
| --------- | ------------------------------------------------- | ------------------------------ |
| Токен     | String                                            | Токен API                      |
| Адрес     | String                                            | Стандартизируемый адрес        |
| Фильтр    | String                                            | Фильтр адреса                  |
| Лимит     | int?                                              | Лимит адресов                  |
| Тайм-аут  | int                                               | Тайм-аут сервера               |
| Результат | Primo.AHunter.Model. StAddress. StandartedAddress | Очищенный адрес                |
| Json      | String                                            | Очищенный адрес в формате JSON |

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.AHunter.AHunterApp ah = new Primo.AHunter.AHunterApp();
string a = ah.StandartizeAddress("token", "address", "Московская область", 10, 10000);
Primo.AHunter.Model.StAddress.StandartedAddress sa = ah.ParseStandartAddress(a);
```
{% endtab %}

{% tab title="Python" %}
```python
ah = Primo.AHunter.AHunterApp()
a = ah.StandartizeAddress("token", "address", "Московская область", 10, 10000) #string
sa = ah.ParseStandartAddress(a) #Primo.AHunter.Model.StAddress.StandartedAddress
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
var ah = host.newObj(_lib.Primo.AHunter.AHunterApp);
var a = ah.StandartizeAddress("token", "address", "Московская область", 10, 10000); //string
sa = ah.ParseStandartAddress(a); //_lib.Primo.AHunter.Model.StAddress.StandartedAddress
```
{% endtab %}
{% endtabs %}
