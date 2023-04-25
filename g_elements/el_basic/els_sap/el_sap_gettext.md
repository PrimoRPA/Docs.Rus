# Получить текст

![](<../../../.gitbook/assets/image (304).png>)

Компонент получает текст выбранного элемента управления. Корректно работает только внутри контейнера SAP.

## Свойства

Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.


| Свойство     | Тип                        | Описание                                           |
| ------------ | -------------------------- | -------------------------------------------------- |
| ***Общие***          | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Процесс*** | |  |
| Окно         | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна - можете воспользоваться инструментом ![](<../../../.gitbook/assets/image (794).png>) для автоматического заполнения свойства при указании на нужный заголовок |
| ID элемента  | String                     | ID элемента                                        |
| Элемент      | LTools.SAP.Model.SAPUIItem | Ссылка на элемент управления                       |
| Обрезка      | -                          | Удаляет пробелы в начале/в конце текста, в зависимости от указанного значения. Доступные значения: 1) No Trim - без обрезки, значение по умолчанию; 2) Trim - обрезает пробелы в начале и в конце текста; 3) Trim Left - обрезает пробелы в начале текста; 4) Trim Right - обрезает пробелы в конце текста |
| Таймаут\*    | Int32                      | Предельное время ожидания завершения процесса (мс). По умолчанию **10000** |
| ***Вывод***  | |  |
| Переменная\* | String                     | Переменная для хранения полученного текста         |


## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
string txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
var txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}
{% endtabs %}
