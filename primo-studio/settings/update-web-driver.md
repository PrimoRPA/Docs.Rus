# Обновление Selenium WebDriver для работы с браузером

Ниже приводится инструкция по обновлению Selenium WebDriver. Шаги являются общими:
* для различных ОС - Windows, Linux, MacOS;
* для различных браузеров - Firefox, Chrome, Edge, Opera, Yandex.

Чтобы обновить веб-драйвер:

1. Проверьте установленную версию вашего браузера на ОС.
2. Проверьте совместимость драйвера и браузера. Например, для Firefox это можно сделать [здесь](https://firefox-source-docs.mozilla.org/testing/geckodriver/Support.html).
3. Скачайте совместимую версию geckodriver для вашей ОС. Например, для РЕД ОС (дистрибутив Linux) и Студии linux x64 обновление можно скачать [здесь](https://github.com/mozilla/geckodriver/releases).

4. Замените geckodriver в папке `<путь до студии>/WebDriver`.

   Пример для Linux:

   ![](../../.gitbook/assets/update-webdriver-linux.png)

   Пример для Windows:

   ![](../../.gitbook/assets/update-webdriver-windows.png)
 
