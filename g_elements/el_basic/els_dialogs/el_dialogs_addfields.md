# Добавить поля журнала

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (243).png>)

![](<../../../.gitbook/assets/Добавить поля журнала.png>)

Позволяет добавить дополнительные поля в журнал Робота Оркестратора. Впоследствии ненужные поля можно удалить при помощи компонента [**Удалить поля журнала**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_dialogs/el\_dialogs\_removefields).

> _Описание общих свойств элемента см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство | Тип                                                                                                                              | Описание                                                                                                              |
| -------- | -------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Поля\*   | [Dictionary\<string, string>](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0) | Массив полей, которые нужно добавить в журнал. Пример: new Dictionary\<string, string>() { { "key", "\\"value\\"" } } |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.AddLogField(wf, new Dictionary<string, string>() { { "key", "\"value\"" } });
```
{% endtab %}

{% tab title="Python" %}
```python
msg = Dictionary[String, String]()
msg.Add("key", "\"value\"")
		LTools.Workflow.PrimoApp.AddLogField(wf, msg
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var msg = host.newObj(_lib.System.Collections.Generic.Dictionary(_lib.System.String, _lib.System.String));
msg.Add("key", "\"value\"");
		_lib.LTools.Workflow.PrimoApp.AddLogField(wf, msg)
```
{% endtab %}
{% endtabs %}
