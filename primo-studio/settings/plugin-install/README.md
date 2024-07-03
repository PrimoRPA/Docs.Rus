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
LTools.WebBrowser.Native.exe install=<browser> lang=<language> mode=<mode> manifest=v3
```
Поддерживаемые аргументы:
* **browser** — тип браузера: CHROME, FIREFOX, EDGE, YANDEX.
* **language** — язык установки: EN, RU.
* **mode** — режим установки расширения. Доступные значения:
  * packed — упакованное;
  * storelocal — из магазина для текущего  пользователя;
  * unpacked — распакованное.
* **manifest** — данный параметр указывается только в случае, если вы хотите, чтобы браузерное расширение взаимодействовало с [Манифестом V3](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3?hl=ru). Переход от Манифеста V2 к Манифесту V3 был протестирован и введен в эксплуатацию. Тем не менее, поскольку расширение на базе Манифеста V3 является новым, рекомендуется сначала проверить работоспособность RPA-проекта в Студии и только затем использовать в Оркестраторе или Robor Runner'е. Манифест V3 поддерживается только для браузеров Chrome, Edge, Yandex. Если параметр не указан, то по умолчанию будет установлено расширение на базе Манифеста V2. 
 
  :small_orange_diamond:***Важно**. Если вы меняете версию Манифеста, сначала удалите расширение на базе старого Манифеста, а затем устанавливайте новое расширение. Переход на расширение на базе Манифеста V3 возможно осуществить до лета 2025 года*.



#### Примеры 

Установка браузерного расширения без интернета:
```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=packed manifest=v3
```

Установка браузерного расширения при наличии интернета:
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

:small_orange_diamond: ***Важно**. При автоматическом способе устанавливается только расширение на базе Манифеста V2*.

