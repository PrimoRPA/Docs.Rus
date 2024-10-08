# Установка расширений и плагинов

Расширения возможно установить:
* [Вручную из Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ruchnaya-ustanovka-iz-studii) — для браузерных расширений и плагинов RDP, Java.
* [Вручную из командной строки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ustanovka-iz-komandnoi-stroki) — для браузерных расширений и плагинов RDP, Java.
* [Автоматически](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension) — только для браузерных расширений на базе манифеста V2.

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
* **manifest** — данный параметр используется только в случае, если вы хотите установить браузерное расширение на базе нового [манифеста V3](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3?hl=ru). Единственное допустимое значение параметра — `v3`. Если параметр manifest не указан, то по умолчанию будет установлено расширение на базе манифеста V2.

  Переход от манифеста V2 к V3 позволит избежать проблем с совместимостью в будущих версиях браузеров на платформе Chromium (Chrome, Yandex, Edge). Однако поскольку это новое решение, то рекомендуется проверять работоспособность проекта с браузерными элементами в Студии перед тем, как добавлять его в Оркестратор или Robor Runner. 

  :large_blue_diamond:***Примечание**. Нумерация версий для расширения на базе манифеста V2 начинается с 1.xx (например, 1.66), на базе V3 — 3.xx (например, 3.66).*
 
  :large_orange_diamond:***Важно**. Если у вас уже установлено расширение, и вы захотели изменить версию манифеста, то сначала удалите расширение на базе старого манифеста и только затем устанавливайте новое*.



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

:large_orange_diamond: ***Важно**. При автоматическом способе устанавливается только расширение на базе манифеста V2 (версии 1.xx)*.

