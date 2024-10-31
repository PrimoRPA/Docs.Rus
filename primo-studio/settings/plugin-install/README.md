# Установка расширений и плагинов

Расширения возможно установить:
* [Вручную из Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ruchnaya-ustanovka-iz-studii) — для браузерных расширений и плагинов RDP, Java.
* [Вручную из командной строки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ustanovka-iz-komandnoi-stroki) — для браузерных расширений и плагинов RDP, Java.
* [Автоматически](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension) — только для браузерных расширений, созданных на основе манифеста V2 (расширение с версией 1.xx).

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
* **manifest** — используется для установки браузерного расширения на основе [манифеста версии 3](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3?hl=ru). Единственное допустимое значение параметра — `v3`. Расширение на базе Manifest V3 разработано, чтобы избежать проблем с совместимостью в поздних версиях браузеров Chrome, Yandex, Edge, основанных на платформе Chromium.  Если параметр `manifest` не указан, то по умолчанию будет установлено расширение для манифеста V2.

{% hint style="info" %}
Версии расширения Primo RPA Extension для Manifest V2 нумеруются с 1.xx (например, 1.66), для Manifest V3 — с 3.xx (например, 3.66).
{% endhint %}

{% hint style="warning" %}
Если вы хотите изменить версию манифеста для установленного расширения, то сначала удалите расширение на базе старого манифеста и только затем устанавливайте новое. Учтите, что для браузера Firefox невозможно установить расширение на базе V3.
{% endhint %}


#### Особенности работы расширения с Manifest V2

Расширение на базе второй версии манифеста (1.xx) на данный момент может работать нестабильно из-за политик Google в отношении старых расширений, не предназначенных для ManifestV3. Чтобы продолжить работу с расширением для Manifest V2, в рабочие контуры рекомендуется добавить политику `ExtensionManifestV2Availability` со значением `2`, которая разрешает пользоваться расширениями на основе Manifest V2.

Например, для браузера Chrome это можно сделать или групповыми политиками или вручную, запустив скрипт от имени администратора на сервере агента (компьютере клиента) в CMD или Powershell:
```
reg add HKLM\SOFTWARE\Policies\Google\Chrome /v ExtensionManifestV2Availability /t REG_DWORD /d 2 /f
```

После этого, [по заявлениям Google](https://chromeenterprise.google/policies/?hl=ru#ExtensionManifestV2Availability), можно будет работать с расширениями второй версии манифеста до июня 2025 года.


#### Пример установки браузерного расширения

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

{% hint style="info" %}
При автоматическом способе устанавливается только расширение на базе манифеста V2 (версия расширения 1.xx).
{% endhint %}

