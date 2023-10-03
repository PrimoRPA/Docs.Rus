# Получить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (19).png>)

![](<../../../../.gitbook/assets/image (269).png>)

**Eng:** Get asset

С помощью этого элемента робот может получить [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) (asset) из Оркестратора. 

**Предварительные условия:**
1. Успешно настроена связь Студии и Оркестратора. О том, как это сделать, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).
2. В Оркестраторе имеются добавленные ресурсы.

Возможно получить ресурс с любым типом данных, заданным на стороне Оркестратора. А именно:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:bangbang: ***Исключение составляет тип данных Credentials. Чтобы получить ресурс с типом Credentials, следует использовать элемент [Получить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getcredentials).***

Полученный ресурс необходимо сохранить в переменную, указанную в свойстве **Результат**. Эта переменная имеет тип данных System.Object.

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Имя ресурса в Оркестраторе, значение которого вы хотите получить. Пример: `"My asset"` |
| Таймаут        | Int32  | Лимит времени выполнения операции в миллисекундах. По умолчанию `5000`. Если по истечении таймаута операция не выполнена, Робот закончит работу с ошибкой |
| Результат      | Object | Имя переменной, которая будет хранить вернувшееся значение ресурса             |

### Обучающий пример

На портале Learning можно скачать процесс [Значения.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%9E%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F.ltw) (либо [Assets.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/En/Orchestrator/Assets/Assets.ltw) - на англ.), демонстрирующий работу элемента. Добавьте этот процесс в свой проект в Студии, чтобы просмотреть его.


### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}
{% endtabs %}
