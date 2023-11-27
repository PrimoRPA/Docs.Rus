  # SecureString к строке

*Eng: SecureStringToString*

![](<../../../.gitbook/assets/SecureString к строке.png>)

Компонент, который преобразует SecureString в строку. Элемент **SecureString к строке** может быть полезен при автоматизации задач, которые требуют обработки конфиденциальных данных. 

### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***Процесс***        |           |              |
| Строка\*             | Строка                 | Укажите переменную строки                 |
| ***Вывод***          |           |              |
| SecureString\*       | [System.Security.SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0) | Укажите переменную вывода, в которую будут сохранены данные в формате SecureString           |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

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
