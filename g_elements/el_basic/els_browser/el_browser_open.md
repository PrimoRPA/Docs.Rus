# Открыть браузер

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (33).png>)

![](<../../../.gitbook/assets/image (293).png>)

Элемент выполняет 2 основные функции:
* Открывает новую вкладку в браузере.
* Выступает в роли контейнера для других элементов, работающих с веб-страницами. Например, для таких как [**Обновить страницу**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_refresh), [**Перейти к странице**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_navigate), [**Клик мышью**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_click) и т. д.

:large_orange_diamond: ***Исключение:** в Internet Explorer будет открываться новый экземпляр браузера, а не вкладка.*

Элементы, вложенные в контейнер **Открыть браузер** и присоединенные к нему, требуют наличия расширения браузера, хотя сам контейнер работает независимо от него. Способы установки браузерных расширений описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install).

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                 | Описание                                                 |
| ------------ | ----------------------------------- | -------------------------------------------------------- |
| Тип браузера | LTools.WebBrowser.Model.BowserTypes | Тип используемого браузера. По умолчанию `IE`. Кликните выпадающий список, чтобы выбрать другое значение |
| Переменная   | LTools.WebBrowser.BrowserInst       | Переменная для сохранения ссылки на подключенный браузер |

### Если вкладка не открылась

Если использование элемента не привело к открытию вкладки, проверьте:

- установлен в системе браузер, выбранный в свойстве **Тип браузера**;
- права доступа пользователя на использование браузера;
- описание ошибки в консоли.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}
{% endtabs %}




