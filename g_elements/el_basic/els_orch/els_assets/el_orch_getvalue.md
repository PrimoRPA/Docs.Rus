# Получить значение

*Eng: Get asset*

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (19).png>)

![](<../../../../.gitbook/assets/image (269).png>)

## Предварительные условия

:white_check_mark: Установлена связь Студии и Оркестратора. О том, как настроить подключение, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).\
:white_check_mark: В Оркестраторе имеются добавленные ресурсы (переменные).

## Назначение

С помощью элемента робот может получить [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) из Оркестратора и использовать в дальнейшей работе. Возможно получить ресурс всех типов данных, кроме Credentials. А именно:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:bangbang: ***Чтобы получить ресурс с типом Credentials, используйте элемент [Получить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getcredentials).***

Вернувшийся в ответе ресурс необходимо сохранить в переменную, указанную в свойстве **Результат**. Эта переменная должна иметь тип данных System.Object.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Название ресурса в Оркестраторе, значение которого хотите получить. Пример: `"My asset"` |
| Таймаут        | Int32  | Лимит времени выполнения операции в миллисекундах. По умолчанию `5000`. Если по истечении таймаута операция не выполнена, робот закончит работу с ошибкой |
| Результат      | Object | Имя переменной для хранения значения ресурса             |


### Решение проблем

![](<../../../../.gitbook/assets1/set-asset-error-in-studio.png>)

При выполнении элемента может возникнуть «Ошибка получения значения». Она возникает, если ресурса с указанным названием нет в Оркестраторе.



## Learning

Чтобы ознакомиться с работой элемента, скачайте обучающий сценарий [Значения.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%9E%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/%D0%97%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D1%8F.ltw) (либо [Assets.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/En/Orchestrator/Assets/Assets.ltw) - на англ.) и добавьте его в свой RPA-проект в Студии для просмотра.


## Только код
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
