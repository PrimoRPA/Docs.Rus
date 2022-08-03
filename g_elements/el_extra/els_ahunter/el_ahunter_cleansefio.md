# Стандартизация ФИО

![](<../../../.gitbook/assets/image (589).png>)



Компонент, производящий стандартизацию ФИО.

Свойства

| Свойство  | Тип                                     | Описание                     |
| --------- | --------------------------------------- | ---------------------------- |
| Токен     | String                                  | Токен API                    |
| ФИО       | String                                  | Стандартизируемое ФИО        |
| Лимит     | int?                                    | Лимит ФИО                    |
| Тайм-аут  | int                                     | Тайм-аут сервера             |
| Результат | Primo.AHunter.Model.StFio.StandartedFio | Очищенное ФИО                |
| Json      | String                                  | Очищенное ФИО в формате JSON |

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.AHunter.AHunterApp ah = new Primo.AHunter.AHunterApp();
string a = ah.StandartizeFio("token", "fio", 10, 10000);
Primo.AHunter.Model.StFio.StandartedFio sa = ah.ParseStandartFio(a);
```
{% endtab %}

{% tab title="Python" %}
```python
ah = Primo.AHunter.AHunterApp()
a = ah.StandartizeFio("token", "fio", 10, 10000) #string
sa = ah.ParseStandartFio(a) #Primo.AHunter.Model.StFio.StandartedFio
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
var ah = host.newObj(_lib.Primo.AHunter.AHunterApp);
var a = ah.StandartizeFio("token", "fio", 10, 10000); //string
sa = ah.ParseStandartFio(a); //_lib.Primo.AHunter.Model.StFio.StandartedFio
```
{% endtab %}
{% endtabs %}
