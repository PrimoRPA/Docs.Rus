# Записать в Credentials

![](<../../../.gitbook/assets/image (402).png>)

Компонент, производящий запись учетных данных в Credential Manager

| Свойство           | Тип     | Описание                                           |
| ------------------ | ------- | -------------------------------------------------- |
| Ключ\*             | String  | Ключ, для поиска записанных данных                 |
| Имя пользователя\* | String  | Имя пользователя                                   |
| Пароль\*           | String  | Пароль                                             |
| Защищать данные    | Boolean | Признак использования дополнительной защиты данных |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", true, "login", "password");
```
{% endtab %}

{% tab title="Second Tab" %}
```python
LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", True, "login", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", true, "login", "password");
```
{% endtab %}
{% endtabs %}
