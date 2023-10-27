# Получить из буфера обмена

*Eng: Get from Clipboard*

Компонент, предназначенный для извлечения данных из буфера обмена.

![](<../../../.gitbook/assets/image (367).png>)


> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство  | Тип    | Описание          |
| --------- | ------ | ----------------- |
| Результат | Object | Получаемые данные |
| Как текст | Boolean | Определяет, нужно ли получать данные в виде текста. Если флаг установлен, то в свойстве **Формат** можно задать формат текста |
| Формат    | -      | Работает только при установке флага **Как текст**. Выберите из выпадающего списка формат, в котором необходимо хранить текст в буфере обмена |


{% tabs %}
{% tab title="C#" %}
```csharp
object obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var obj = _lib.LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}
{% endtabs %}

