# SecureString к строке

![](<../../../.gitbook/assets/SecureString к строке.png>)

Компонент, преобразующий SecureString к строке.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| Строка\*             | String                | Строковая переменная                          |
| SecureString\*       | [System.Security.SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0) | Переменная, в которой будут сохранены данные в формате SecureString           |


**Пример работы элемента можно посмотреть [здесь](https://github.com/PrimoRPA/Learning/tree/master/Ru/%D0%9A%D1%80%D0%B8%D0%BF%D1%82%D0%BE%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D1%8F).**



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
