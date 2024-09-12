# JSON к объекту

*Eng: Json to object*

![](<../../../../.gitbook/assets/image (255).png>)

Компонент выполняет преобразование строки в формате JSON в объект .NET.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| *Свойство*     | *Тип*    | *Описание*                                                                                                                                         |
| ---------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Вывод:**     |           |                                                                               |
| Переменная*    |[Newtonsoft.Json.Linq.JObject] | Переменная, в которую будет сохранён результат преобразования JSON в объект.   |
| **Обработка:** |           |                                                                               |
| Данные*        | String  | Строка JSON, которую нужно преобразовать в объект. Может быть указана как строковая переменная. |

Узнать подробнее о преобразования текста JSON в объект можно [здесь](https://www.newtonsoft.com/json/help/html/Introduction.htm).


###  Пример использования элемента на Learning

Для изучения работы с элементом *JSON к объекту*, вы можете скачать обучающий RPA-проект в нашем публичном репозитории Learning по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip)

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект StudioActivities в Студии.
3. Найдите процесс StudioActivities/Ru/Данные/JSON/JSON.ltw для изучения работы элемента.


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
