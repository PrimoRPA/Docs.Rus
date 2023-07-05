# JSON к объекту

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (130).png>)

![](<../../../../.gitbook/assets/image (255).png>)

Компонент осуществляет преобразование JSON в объект .NET.

Узнать подробнее о преобразования текста JSON в объект можно [здесь](https://www.newtonsoft.com/json/help/html/Introduction.htm).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство     | Тип     | Описание                                                                                       |
| ------------ | ------- | ---------------------------------------------------------------------------------------------- |
| ***Обработка:*** | | |
| Данные\*     | String  | Строка JSON, которую нужно преобразовать в объект. Может быть указана как строковая переменная |
| ***Вывод:*** | | |
| Переменная\* | dynamic | Переменная вывода, получающая результирующий объект                                            |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
dynamic ret = Newtonsoft.Json.JsonConvert.DeserializeObject("json");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = Newtonsoft.Json.JsonConvert.DeserializeObject("json")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.Newtonsoft.Json.JsonConvert.DeserializeObject("json");
```
{% endtab %}
{% endtabs %}
