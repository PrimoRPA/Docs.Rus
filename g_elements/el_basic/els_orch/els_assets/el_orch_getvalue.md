# Получить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (19).png>)

![](<../../../../.gitbook/assets/image (269).png>)

С помощью элемента робот может получить [ресурс (asset)](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) из Оркестратора. Поддерживается получение ресурсов со следующими типами данных:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:bangbang: ***Чтобы получить ресурс с типом Credentials, следует использовать элемент [Получить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getcredentials).***

Вернувшийся в ответе ресурс необходимо сохранить в переменную, указанную в свойстве **Результат**. Эта переменная должна иметь тип данных System.Object.

### Предварительные условия

:heavy_check_mark: Установлена связь Студии и Оркестратора. Как настроить подключение, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).\
:heavy_check_mark: В Оркестраторе имеются добавленные ресурсы.


### Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Имя ресурса в Оркестраторе, значение которого вы хотите получить. Пример: `"My asset"` |
| Таймаут        | Int32  | Лимит времени выполнения операции в миллисекундах. По умолчанию `5000`. Если по истечении таймаута операция не выполнена, робот закончит работу с ошибкой |
| Результат      | Object | Имя переменной для хранения значения ресурса             |


### Пример на Learning

Скачайте обучающий процесс [Значения.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%9E%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F.ltw) (либо [Assets.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/En/Orchestrator/Assets/Assets.ltw) - на англ.). Добавьте его в свой проект в Студии, чтобы просмотреть работу элемента.


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
