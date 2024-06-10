# Установка расширений и плагинов

Расширения возможно установить:
* [вручную из Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ruchnaya-ustanovka-iz-studii) — для браузерных расширений и плагинов RDP, Java;
* [вручную из командной строки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ustanovka-iz-komandnoi-stroki) — для браузерных расширений и плагинов RDP, Java;
* [автоматически](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension) — только для браузерных расширений.

## Ручная установка из Студии

Инструкции см. в разделах:

{% content-ref url="chrome.md" %}
[chrome.md](chrome.md)
{% endcontent-ref %}

{% content-ref url="firefox.md" %}
[firefox.md](firefox.md)
{% endcontent-ref %}

{% content-ref url="edge.md" %}
[edge.md](edge.md)
{% endcontent-ref %}

{% content-ref url="yandex.md" %}
[yandex.md](yandex.md)
{% endcontent-ref %}

{% content-ref url="rdp.md" %}
[rdp.md](rdp.md)
{% endcontent-ref %} 

{% content-ref url="java.md" %}
[java.md](java.md)
{% endcontent-ref %}


## Установка из командной строки

Ниже приводятся способы установки расширений и плагинов из командной строки.

### Расширения браузеров

```
LTools.WebBrowser.Native.exe install=<browser> lang=<language> mode=<mode>
```
Поддерживаемые аргументы:
* **browser** — тип браузера: CHROME, FIREFOX, EDGE, YANDEX.
* **language** — язык установки: EN, RU.
* **mode** — режим установки расширения. Доступные значения:
  * packed — упакованное;
  * storelocal — из магазина для текущего  пользователя;
  * unpacked — распакованное.
* **manifest** — версия Манифеста, с которой взаимодействовать браузерному приложению. Данный параметр указывается только в случае использования Манифеста V3. Если параметр не указан, то по умолчанию будет установлено приложение на базе Манифеста V2. Новый Манифест поддерживается для браузеров Chrome, Edge, Yandex.
 
  :small_orange_diamond: ***Важно**. Если вы меняете версию Манифеста, сначала удалите расширение на базе старого Манифеста, а только затем устанавливайте новое расширение*.

Пример установки без интернета:
```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=packed manifest=v3
```

Пример установки при наличии интернета:
```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=storelocal manifest=v3
```

### Плагины

#### RDP

```
Primo.RemoteAgent.exe InstallClient
```

#### Java

```
Extensions\JavaBridge.ps1
```


## Автоматическая установка браузерных расширений

Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension).

