# Должен остановиться

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (153).png>)

![](<../../../../.gitbook/assets/image (282).png>)

Компонент, который получает сигнал остановки из Оркестратора.

| Свойство    | Тип     | Описание                                  |
| ----------- | ------- | ----------------------------------------- |
| Результат\* | Boolean | Переменная для хранения полученных данных |
| Таймаут     | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |

{% tabs %}
{% tab title="C#" %}
```csharp
bool ret = LTools.Enterprise.OrchestratorApp.ShouldStop(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.ShouldStop(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.ShouldStop(wf);
```
{% endtab %}
{% endtabs %}
