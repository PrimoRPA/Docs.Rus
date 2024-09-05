# МойОфис Текст

![](<../../../../.gitbook/assets/image (938).png>)

Контейнер производит подключение к приложению [МойОФис Текст](https://myoffice.ru/apps/text/). В случае отсутствия указанного файла, будет создан новый.

## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство      | Тип     | Описание                                           |
| ------------- | ------- | -------------------------------------------------- |
| Путь к файлу  | String  | Путь к файлу документа Текст (c:\folder\file.docx) |
| Массив байтов | byte\[] | Массив байтов документа                            |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MyOfficeTextApp app = LTools.Office.MyOfficeTextApp.Init(wf, fileName, [interop]);
LTools.Office.MyOfficeTextApp app = LTools.Office.MyOfficeTextApp.Init(wf, bytes);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MyOfficeTextApp.Init(wf, fileName) #LTools.Office.MyOfficeTextApp
app = LTools.Office.MyOfficeTextApp.Init(wf, bytes) #LTools.Office.MyOfficeTextApp
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.MyOfficeTextApp.Init(wf, fileName); //_lib.LTools.Office.MyOfficeTextApp
let app = _lib.LTools.Office.MyOfficeTextApp.Init(wf, bytes); //_lib.LTools.Office.MyOfficeTextApp
```
{% endtab %}
{% endtabs %}
