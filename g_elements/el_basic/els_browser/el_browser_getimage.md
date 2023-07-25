# Скачать изображение

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (319).png>)

![](<../../../.gitbook/assets/image (355).png>)

Компонент, производящий получение изображения. Компонент корректно работает только внутри контейнера "Открыть браузер" либо "Присоединиться к браузеру".

| Свойство      | Тип                                  | Описание                                                           |
| ------------- | ------------------------------------ | ------------------------------------------------------------------ |
| Шаблон поиска | String                               | Шаблон поиска элемента управления                                  |
| Элемент       | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                                       |
| Атрибут       | String                               | Название атрибута элемента управления, содержащего URL изображения |
| Изображение\* | byte\[]                              | Переменная для сохранения данных полученного изображения           |
| URL           | String                               | URL изображения                                                    |
| Таймаут\*     | Int32                                | Предельное время ожидания завершения процесса (мс)                 |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//По атрибуту
byte[] img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src");	
//По URL
img = LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg");
System.IO.File.WriteAllBytes(@"C:\image.png", img);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#По атрибуту
img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src")
#По URL
img = LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg")
System.IO.File.WriteAllBytes("C:\\image.png", img)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//По атрибуту
var img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src");	
//По URL
img = _lib.LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg");
_lib.System.IO.File.WriteAllBytes("C:\\image.png", img);
```
{% endtab %}
{% endtabs %}
