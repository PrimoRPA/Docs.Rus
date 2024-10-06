---
description: Get processes
---

# Список процессов

![](<../../../.gitbook/assets/image (125).png>)

Элемент получает список процессов запущенных приложений рабочего стола. В свойствах элемента возможно указать, хотите ли вы получить все процессы или только процессы текущего пользователя. Список процессов будет сохранен в указанную переменную.

## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Процесс:**

1. **Текущий пользователь** *[bool]* — определяет, следует ли получать процессы только текущего пользователя. По умолчанию не используется — в переменную сохранятся запущенные процессы всех пользователей.
1. **Имя процесса** *[String]* — шаблон поиска по имени определенного процесса. Пример: `"Primo\*"`. Если шаблон не указан, получены будут все запущенные процессы.


**Вывод:**

* **Переменная\*** [List\<System.Diagnostics.Process>] — название переменной для хранения полученного списка процессов.


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Ru > Рабочий стол > Список процессов.ltw` для просмотра.




## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
