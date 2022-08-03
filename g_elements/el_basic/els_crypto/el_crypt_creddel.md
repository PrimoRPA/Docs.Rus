# Удалить Credentials

![](<../../../.gitbook/assets/image (313).png>)

Компонент, производящий удаление учетных данных из Credential Manager

| Свойство | Тип    | Описание                           |
| -------- | ------ | ---------------------------------- |
| Ключ\*   | String | Ключ, для поиска записанных данных |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key");
```
{% endtab %}
{% endtabs %}
