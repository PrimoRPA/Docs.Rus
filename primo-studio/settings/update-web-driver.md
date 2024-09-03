# Обновление Selenium WebDriver 

Ниже приводится инструкция по обновлению Selenium WebDriver для работы с браузером. Шаги являются общими:
* для ОС Windows, Linux, MacOS;
* для браузеров Firefox, Chrome, Edge, Opera, Yandex.

**Чтобы обновить веб-драйвер:**

1. Проверьте установленную версию вашего браузера на ОС. Убедитесь, что у вас установлена последняя версия браузера, с которым вы планируете работать. Для этого перейдите в раздел "О программе" (обычно находится в меню настроек браузера). 
2. Проверьте, что версия веб-драйвера совместима с версией вашего браузера. Например, для Firefox совместимые версии драйверов можно найти [на официальной странице Geckodriver](https://firefox-source-docs.mozilla.org/testing/geckodriver/Support.html).
3. Скачайте совместимую версию Webdriver для вашей ОС. Пример:
   * [для Firefox](https://github.com/mozilla/geckodriver/releases);
   * [для Chrome](https://chromedriver.chromium.org/downloads);
   * [для Edge](https://developer.microsoft.com/ru-ru/microsoft-edge/tools/webdriver/);
   * [для Yandex](https://github.com/yandex/YandexDriver);
   * [для Opera](https://github.com/operasoftware/operachromiumdriver).

4. После загрузки замените текущий драйвер в папке <путь до студии>/WebDriver на новую версию.
   - Например, для Firefox замените geckodriver.exe на новую версию.

   * Пример для Linux:

   ![](../../.gitbook/assets/update-webdriver-linux.png)

   * Пример для Windows:

   ![](../../.gitbook/assets1/new_web_driver.png)


### Улучшения в версии 1.24.8:

   - В комплекте с Primo RPA Studio 1.24.8 новые версии веб-драйверов (Chrome, Yandex, Firefox (Gecko), Edge, Opera).
   - Пути в WDBrowser были изменены, чтобы драйвера обновлялись с актуальными именами файлов.
   - Обновление пакета Selenium.WebDriver. Пакеты были обновлены в связи с изменениями в расположении бинарных файлов между версиями Firefox 120 и 121.

Важно, чтобы версия веб-драйвера точно соответствовала версии браузера. Использование более свежего веб-драйвера может привести к некорректной работе, если браузер давно не обновлялся.
 
