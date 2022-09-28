# SecureString к строке

![](<../../../.gitbook/assets/SecureString к строке.png>)

Компонент, преобразующий SecureString к строке.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| Строка\*             | String                | Строковая переменная                          |
| SecureString\*       | [System.Security.SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0) | Переменная, в которой будут сохранены данные в формате SecureString           |


{% tabs %}
{% tab title="C#" %}
```csharp
string ret = Common.Helpers.CryptographyHelper.SecureStringToString("txt");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = Common.Helpers.CryptographyHelper.SecureStringToString("txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.Common.Helpers.CryptographyHelper.SecureStringToString("txt");
```
{% endtab %}
{% endtabs %}
