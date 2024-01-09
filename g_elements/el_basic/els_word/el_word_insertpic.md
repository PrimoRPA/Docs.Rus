# Вставка изображения

*Eng: Insert image*

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (249).png>)

![](<../../../.gitbook/assets/image (204).png>)

Элемент производит вставку изображения в документ Word. Путь до документа указывается в контейнере [Документ Word](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_word/el_word_app?q=%D0%94%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82+Word).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство      | Тип     | Описание                                                                                      |
| ------------- | ------- | --------------------------------------------------------------------------------------------- |
| Изображение\* | byte\[] | Вставляемое изображение                                                                       |
| Закладка      | String  | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Позиция       | Int32   | Позиция для вставки. Добавлено в версии Студии 23.11                                          |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.InsertPicture(System.IO.File.ReadAllBytes("file"), "bookmark");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.InsertPicture(System.IO.File.ReadAllBytes("file"), "bookmark")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.InsertPicture(_lib.System.IO.File.ReadAllBytes("file"), "bookmark");
```
{% endtab %}
{% endtabs %}
