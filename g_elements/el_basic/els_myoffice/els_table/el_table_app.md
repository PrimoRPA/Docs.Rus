# МойОфис Таблица

![](<../../../../.gitbook/assets/image (529).png>)

Контейнер, который производит подключение к приложению МойОфис Таблицы. В случае отсутствия указанного файла, будет создан новый.

## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство      | Тип     | Описание                                             |
| ------------- | ------- | ---------------------------------------------------- |
| Путь к файлу  | String  | Путь к файлу документа МойОфис (c:\folder\file.xlsx) |
| Массив байтов | byte\[] | Массив байтов документа                              |
| Кодовая страница | int? | Кодовая страница кириллицы                           |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MyOfficeTableApp app = LTools.Office.MyOfficeTableApp.Init(wf, fileName);
LTools.Office.MyOfficeTableApp app = LTools.Office.MyOfficeTableApp.Init(wf, bytes);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MyOfficeTableApp.Init(wf, fileName) #LTools.Office.MyOfficeTableApp
app = LTools.Office.MyOfficeTableApp.Init(wf, bytes) #LTools.Office.MyOfficeTableApp
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.MyOfficeTableApp.Init(wf, fileName); //_lib.LTools.Office.MyOfficeTableApp
let app = _lib.LTools.Office.MyOfficeTableApp.Init(wf, bytes); //_lib.LTools.Office.MyOfficeTableApp
```
{% endtab %}
{% endtabs %}
