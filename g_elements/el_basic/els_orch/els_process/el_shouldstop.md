# Должен остановиться

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (153).png>)

![](<../../../../.gitbook/assets/image (282).png>)

**Должен остановиться (Should stop)** - компонент, который получает сигнал остановки из Оркестратора. 

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство    | Тип     | Описание                                  |
| ----------- | ------- | ----------------------------------------- |
| Таймаут     | Int32   | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| Результат\* | Boolean | Переменная для хранения полученных данных |

:bangbang: **Внимание!** Чтобы Робот не заканчивал работу с ошибкой типа *Ошибка при обращении к Оркестратору*:
- включите чекбокс **Продолжить при ошибке** в группе общих свойств;
- либо используйте этот элемент в [Try-Catch](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/el_logic_trycatch). 
 
С версии Робота 23.6 данный вид ошибки будет игнорироваться по умолчанию, т.е. чекбокс можно не включать.

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

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
