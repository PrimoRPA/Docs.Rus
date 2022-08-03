# Прочитать Credentials

![](<../../../.gitbook/assets/image (196).png>)

Компонент, производящий прочитать учетные данные из Credential Manager

| Свойство        | Тип                          | Описание                                           |
| --------------- | ---------------------------- | -------------------------------------------------- |
| Ключ\*          | String                       | Ключ, для поиска записанных данных                 |
| Текст\*         | LTools.Common.Model.UserPass | Переменная для хранения полученных данных          |
| Защищать данные | Boolean                      | Признак использования дополнительной защиты данных |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Common.Model.UserPass ret = LTools.Cryptography.CryptoApp.CredentialsGet(wf, "Key", true);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Cryptography.CryptoApp.CredentialsGet(wf, "Key", True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Cryptography.CryptoApp.CredentialsGet(wf, "Key", true);
```
{% endtab %}
{% endtabs %}
