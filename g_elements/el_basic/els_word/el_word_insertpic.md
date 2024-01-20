# Вставка изображения

*Eng: Insert image*

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (249).png>)

![](<../../../.gitbook/assets/image (204).png>)

Элемент производит вставку изображения в документ Word. Путь до документа указывается в контейнере [Документ Word](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_word/el_word_app?q=%D0%94%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82+Word).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Изображение\*** *[[byte[]](https://learn.microsoft.com/ru-ru/dotnet/api/system.byte?view=net-8.0&viewFallbackFrom=net-4.6.1)]*: Название переменной, которая содержит изображение для вставки. 
2. **Закладка** *[String]*: Имя закладки, определяющей начало записи. Если закладка не указана, вставка производится в конец текста.
3. **Позиция** *[Int32]*: Позиция для вставки изображения, указывается в символах. Позицию можно указать, например, относительно какого-либо слова в тексте. Для этого сначала [найдите слово](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_word/el_word_find) в документе, а затем укажите количество символов до или после него. Пример заполнения см. в учебном проекте.


## Learning

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, демонстрирующий работу элемента.

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities/Ru/Приложение Word/Вставка изображения.ltw` для просмотра.

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
