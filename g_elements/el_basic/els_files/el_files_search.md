# Поиск файлов

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (203).png>)

![](<../../../.gitbook/assets/image (199).png>)

Элемент, осуществляющий поиск файлов и папок.

| Свойство        | Тип           | Описание                                           |
| --------------- | ------------- | -------------------------------------------------- |
| Путь\*          | String        | Путь поиска файлов. Пример: `@"C:\Directory"`      |
| Шаблон          | String        | Шаблон поиска файлов (\*_.\*_)                     |
| Искать в папках | Boolean       | Признак поиска в папках                            |
| Переменная\*    | List\<String> | Переменная для сохранения найденных путей к файлам |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
string[] files = System.IO.Directory.GetFiles(@"C:\", "*.txt", System.IO.SearchOption.AllDirectories);
```
{% endtab %}

{% tab title="Python" %}
```python
files = System.IO.Directory.GetFiles("C:\\", "*.txt", System.IO.SearchOption.AllDirectories)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var files = _lib.System.IO.Directory.GetFiles("C:\\", "*.txt", _lib.System.IO.SearchOption.AllDirectories);
```
{% endtab %}
{% endtabs %}
