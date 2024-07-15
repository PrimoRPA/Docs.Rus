# Фильтр диапазона

*Eng: Filter Range*

![](<../../../.gitbook/assets/image (265).png>)

Элемент устанавливает фильтр диапазона ячеек Excel.

## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип           | Описание                                                                               |
| --------------- | ------------- | -------------------------------------------------------------------------------------- |
| Диапазон\*      | String        | Диапазон считывания ячеек. Пример: `"A1:D12"`. Если не указан, будет прочитан выделенный диапазон |
| Страница        | String        | Название страницы. Пример: `"Лист1"`                                                   |
| Индекс страницы | Int32         | Порядковый номер страницы, нумерация ведется с нуля. Пример: `0`                       |
| Фильтр\*        | List\<string> | Значения фильтра                                                                       |

## Дополнительно

Расширена поддержка множественных критериев фильтрации:
В Primo RPA Studio с версии 24.4 добавлена возможность фильтрации по нескольким критериям одновременно, что улучшает гибкость работы с данными Excel. В ранних версиях элемент **Filter Range** поддерживал фильтрацию только по одному критерию. 

Введение ограничений на использование символов замещения:
При использовании до двух критериев включительно можно применять символы замещения `*` и `?`. Если критериев более двух, необходимо использовать точное совпадение значений. 


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


