# Список процессов

![](<../../../.gitbook/assets/image (125).png>)

Компонент, получающий список запущенных процессов, всех или текущего пользователя.

| Свойства             | Тип                               | Описание                                                 |
| -------------------- | --------------------------------- | -------------------------------------------------------- |
| Текущий пользователь | bool                              | Признак получения только процессов текущего пользователя |
| Имя процесса         | String                            | Шаблон поиска имени процесса (calc\*)                    |
| Переменная\*         | List\<System.Diagnostics.Process> | Переменная для хранения полученного списка               |

{% tabs %}
{% tab title="C#" %}
```csharp
List<System.Diagnostics.Process> proc = LTools.Desktop.DesktopApp.GetProcesses(wf, true);
foreach (var p in proc)
	LTools.Workflow.PrimoApp.AddToLog(wf, p.ProcessName);
```
{% endtab %}

{% tab title="Python" %}
```python
proc = LTools.Desktop.DesktopApp.GetProcesses(wf, True)
for p in proc:
	LTools.Workflow.PrimoApp.AddToLog(wf, p.ProcessName)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var proc = _lib.LTools.Desktop.DesktopApp.GetProcesses(wf, true);
for (var i = 0; i < proc.Count; i++)
	_lib.LTools.Workflow.PrimoApp.AddToLog(wf, proc[i].ProcessName);
```
{% endtab %}
{% endtabs %}
