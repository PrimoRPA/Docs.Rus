# Установка расширений и плагинов

Расширения возможно установить:
* [автоматически](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension) - только для браузерных расширений;
* вручную из Студии - для браузерных расширений и плагинов RDP, Java;
* из командной строки - для браузерных расширений и плагинов RDP, Java.

## Установка из Студии

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

## Расширения браузеров

```
LTools.WebBrowser.Native.exe install=[browser] lang=[language] mode=[mode]
```
Поддерживаемые аргументы:
* **browser** - тип браузера (CHROME, FIREFOX, EDGE, YANDEX);
* **language** - язык установки (EN, RU);
* **mode** - режим установки (store, packed, unpacked, storelocal).

## Плагины

### RDP

```
Primo.RemoteAgent.exe InstallClient
```

### Java

```
Extensions\JavaBridge.ps1
```




