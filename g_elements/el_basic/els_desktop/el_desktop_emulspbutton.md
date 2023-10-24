# Эмуляция спецкнопки

*Eng: Hot-key simulation*

Предназначен для эмуляции нажатия клавиш клавиатуры или их комбинаций. Этот элемент часто используется для автоматизации действий, требующих ввода с клавиатуры.

Для надежности рекомендуется использовать этот элемент в контейнере [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach).

![](<../../../.gitbook/assets/image (149).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 

#### Группа «Общие» 

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Группа «Новое ядро»

:large_orange_diamond: *Значения этих свойств учитываются, только если установлен чекбокс **Новое ядро***.

![](<../../../.gitbook/assets/hot-key-emul-new-core-parameters.png>)

Предоставляют возможность выбрать клавишу, которая будет эмулирована в процессе выполнения:

1. **Новое ядро**. Boolean. Признак использования нового ядра для взаимодействия с операционной системой. Установите галочку, если новое ядро нужно использовать. По умолчанию галочка снята.
1. **Основная кнопка**. LTools.Common.Model.VirtualKey. Клавиша, которая будет эмулирована. По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать клавишу. Пример: `F2`.
1. **Модификатор**. LTools.Common.Model.VirtualKey. Кнопка-модификатор, которая позволяет добавить к основной клавише дополнительные функции (например, Ctrl, Shift, Alt). По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать модификатор. Пример: `Shift`.
1. **Дополнительная кнопка**. LTools.Common.Model.VirtualKey. Позволяет указать вторую клавишу в комбинации, если она требуется. По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать кнопку. Пример: `Tab`.

#### Группа «Процесс»

:large_orange_diamond: *Значения этих свойств проигнорируются, если установлен чекбокс **Новое ядро***. 

![](<../../../.gitbook/assets/hot-key-emul-proccess-parameters-2.png>)

Предназначены для указания комбинации клавиш для эмуляции: 

1. **Спецкнопки**. String. Нажимаемые спецкнопки. По умолчанию `"{ENTER}"`. С перечнем спецкнопок можно ознакомиться [на сайте Microsoft](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send).

    Убедитесь, что установлен **Режим без кода (выкл)**. Иначе могут возникнуть непредвиденные символы.

    ![](<../../../.gitbook/assets/hot-key-emul-no-code.png>)

1. **Асинхронный**. Boolean. Определяет тип ввода: синхронный или асинхронный. По умолчанию галочка не установлена - используется синхронный ввод. Отличия:
   * Синхронный - в этом режиме кнопки нажимаются одновременно. Например, если нужно нажать Ctrl + A, то обе клавиши активируются в один момент времени.
   * Асинхронный - в этом режиме между последовательными нажатиями происходит пауза. Например, при задержке в 500 миллисекунд будет сначала нажата первая клавиша, а через 500 мс - вторая.
1. **Пауза\***. Int32. Пауза перед и после нажатия кнопок в миллисекундах. По умолчанию `500`.
1. **Таймаут\***. Int32. Предельное время ожидания завершения процесса в миллисекундах. По умолчанию `10000`.

### Пример эмуляции

Пример для эмуляции комбинации клавиш `Ctrl` + `A`.

С использованием **Нового ядра**:

* Новое ядро: Включено
* Основная кнопка: A
* Модификатор: Ctrl

С использованием **Спецкнопки**:

* Новое ядро: Выключено
* Спецкнопки: `"^A"`

**Рекомендации:**

Для эмуляции нажатия клавиши `"("` используйте команду `"{(}"`. Аналогичным образом для символа `")"` используйте `"{)}"`.

Для эмуляции нажатия сочетания клавиш `Ctrl` + `Shift` + `N` установите следующие параметры в свойствах элемента:

* Новое ядро: Выключено (если активировано, то команда может не сработать).
* Спецкнопки: `"^n"`.


#### Спецкнопки

Перечень с некоторыми значениями для эмуляции спецкнопок:

1. BACKSPACE: "{BACKSPACE}", "{BS}", or "{BKSP}"
2. BREAK: "{BREAK}"
3. CAPS LOCK: "{CAPSLOCK}"
4. DELETE: "{DELETE}" or "{DEL}"
5. DOWN ARROW: "{DOWN}"
6. END: "{END}"
7. ENTER: "{ENTER}" or "~"
8. ESC: "{ESC}"
9. HELP: "{HELP}"
10. HOME: "{HOME}"
11. INSERT: "{INSERT}" or "{INS}"
12. LEFT ARROW: "{LEFT}"
13. NUM LOCK: "{NUMLOCK}"
14. PAGE DOWN: "{PGDN}"
15. PAGE UP: "{PGUP}"
16. PRINT SCREEN: "{PRTSC}" (reserved for future use)
17. RIGHT ARROW: "{RIGHT}"
18. SCROLL LOCK: "{SCROLLLOCK}"
19. TAB: "{TAB}"
20. UP ARROW: "{UP}"
21. F1: "{F1}"
22. F2: "{F2}"
23. F3: "{F3}"
24. F4: "{F4}"
25. F5: "{F5}"
26. F6: "{F6}"
27. F7: "{F7}"
28. F8: "{F8}"
29. F9: "{F9}"
30. F10: "{F10}"
31. F11: "{F11}"
32. F12: "{F12}"
33. F13: "{F13}"
34. F14: "{F14}"
35. F15: "{F15}"
36. F16: "{F16}"
37. Keypad add: "{ADD}"
38. Keypad subtract: "{SUBTRACT}"
39. Keypad multiply: "{MULTIPLY}"
40. Keypad divide: "{DIVIDE}"


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
_lib.LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}
{% endtabs %}
