# Установка расширений и плагинов

В статье приводится способ установки расширений и плагинов из командной строки.

## Расширения браузеров

```
LTools.WebBrowser.Native.exe install=[browser] lang=[language] mode=[mode]
```
Поддерживаемые аргументы:
* **browser** - тип браузера (CHROME, FIREFOX, EDGE, YANDEX);
* **language** - язык установки (EN, RU);
* **mode** - режим установки (store, packed, unpacked, storelocal).

## Установка плагинов

### RDP

```
Primo.RemoteAgent.exe InstallClient
```

### Java

```
Extensions\JavaBridge.ps1
```


## Установка плагинов из Студии

Перечисленные плагины также можно установить напрямую из Студии. Инструкции см. в разделах:

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

