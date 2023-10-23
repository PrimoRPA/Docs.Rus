#  Закрыть браузер 
# **CloseBrowser**


![](<../../../.gitbook/assets/image (377).png>)

Компонент, завершающий работу браузера. Компонент корректно работает только внутри контейнера "Открыть браузер" либо "Присоединиться к браузеру".

Данный элемент может быть полезен, когда необходимо завершить работу с веб-браузером после выполнения всех необходимых действий. 
Например, после того как собраны все нужные данные с веб-страницы, закрытие браузера поможет освободить ресурсы и завершить текущий процесс робота.

Свойства элемента:

 **Продолжить при исключении (Continue on Exception)**: Данный параметр определяет, следует ли продолжить выполнение процесса в случае возникновения исключения во время закрытия браузера.

 **Отключить журналирование (Disable Logging)**: Если этот параметр включен, то действие не будет записано в лог робота. 

 **Ожидание после (Wait After)**: Этот параметр позволяет установить задержку (в миллисекундах) после выполнения активности "Закрыть браузер". 

 **Ожидание перед (Wait Before)**: Этот параметр определяет задержку (в миллисекундах) перед выполнением активности "Закрыть браузер". Это может быть полезно, чтобы убедиться, что все предыдущие действия завершены перед закрытием браузера.


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Close();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Close()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Close();
```
{% endtab %}
{% endtabs %}
