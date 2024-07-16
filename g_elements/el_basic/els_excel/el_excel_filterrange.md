# Фильтр диапазона

*Eng: Filter Range*

![](<../../../.gitbook/assets/image (265).png>)

Элемент устанавливает один или несколько фильтров в заданном диапазоне ячеек Excel. Фильтр не поддерживает операторы сравнений, фильтрация осуществляется по совпадению значения со значением, указанным в фильтре. Использование фильтра позволяет отобразить в документе нужные данные и временно скрывает остальные. 

Путь до файла Excel настраивается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). При необходимости сохранить изменения в файле, используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон\*** *[String]* — диапазон ячеек для фильтрации. Пример: `"B1:B12"`. Если диапазон не указан, будет отфильтрован выделенный диапазон.
1. **Фильтр\***  *[List\<string>]* — значения фильтра. Откройте редактор коллекций по иконке таблицы:

   ![](<../../../.gitbook/assets1/windows_items/ExcelWFFilterRange-open-editor.png>)

   Введите условие фильтрации в строку, обернув его кавычками, поскольку фильтр имеет тип данных String: 

   ![](<../../../.gitbook/assets1/windows_items/ExcelWFFilterRange-editor-value.png>)

   Чтобы добавить еще один фильтр, нажмите `Enter` и введите новое значение в следующей строке. Если вы используете не более двух условий фильтрации, то можете применять в них следующие символы замещения:
   * Символ `*` — замещает любое количество символов. Пример: `"ИП*"`.
   * Символ `?`—  замещает только один символ. 
   
   Если условий более двух, необходимо использовать точное совпадение значений.
   
1. **Страница** *[String]* — название страницы, если документ имеет несколько листов. Пример: `"Лист1"`.
1. **Индекс страницы** *[Int32]* — порядковый номер страницы, если документ имеет несколько листов. Нумерация ведется с нуля. Пример: `0`.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.FilterRange(new List<string>(), "A1:C12", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.FilterRange(List[String](), "A1:C12", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.FilterRange(lst, "A1:C12", "Лист1");
```
{% endtab %}
{% endtabs %}


