# Восстановить окно

*Eng: Restore window*

![](<../../../.gitbook/assets/image (241).png>)

Элемент, восстанавливающий окно приложения. Компонент корректно работает только внутри контейнера **Присоединиться к приложению**. Используется в сценариях, где необходимо вернуть окно приложения в нормальное состояние для дальнейшего взаимодействия.

### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс) |


###  Пример Learning

Для изучения работы с элементом **Восстановить окно**, вы можете скачать обучающий RPA-проект по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip)

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект `StudioActivities` в Студии.
3. Найдите процесс `StudioActivities/Ru/Рабочий стол/Активировать Свернуть Развернуть Восстановить.ltw` для изучения работы элемента.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "*Notepad*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Restore();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "*Notepad*", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Restore()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "*Notepad*", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Restore();
```
{% endtab %}
{% endtabs %}
