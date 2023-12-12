# HTML to DataTable

 Элемент предназначен для преобразования HTML-кода в коллекцию таблиц, полезно в случаях, когда требуется извлечь таблицы из HTML-кода, например, из тела письма. 
 Он эффективно обрабатывает HTML, содержащий одну или более таблиц. Важно отметить, что элемент работает исключительно с таблицами; 
 любой другой контент в HTML-коде, не являющийся таблицей, в результате преобразования отображаться не будет.


![](<../../../../.gitbook/assets1/data_table9.png>)


**Свойства:**

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

- **Группа «Output»:**
  -  **Tables\*:** `System.Collections.Generic.List<System.Data.DataTable>`. Эта переменная содержит результат выполнения активности, а именно коллекцию таблиц.

- **Группа «Processing»:**
  -  **HTML\*:** `System.String`. Переменная, содержащая строку с HTML-кодом. Пример HTML-кода: `<table><tr><th>текст заголовка1</th><th>текст заголовка2</th></tr><tr><td>данные1</td><td>данные2</td></tr></table>`.


![](<../../../../.gitbook/assets1/1.png>)


![](<../../../../.gitbook/assets1/processing.png>)


## Learning

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, демонстрирующий работу элемента.

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities/En/Data/HTML/HtmlToDataTable.ltw`для просмотра.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
//Element that extracts DataTables from HTML document.  Properties
//html - HTML: [String] HTML document
List<System.Data.DataTable> ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html);
```
{% endtab %}

{% tab title="Python" %}
```python
#Element that extracts DataTables from HTML document.  Properties
#html - HTML: [String] HTML document
ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html) #List<System.Data.DataTable>
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Element that extracts DataTables from HTML document.  Properties
//html - HTML: [String] HTML document
var ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html) #List<System.Data.DataTable>
```
{% endtab %}
{% endtabs %}
