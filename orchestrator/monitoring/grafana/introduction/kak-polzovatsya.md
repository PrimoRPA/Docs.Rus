# Как пользоваться

Результаты мониторинга Primo RPA Orchestrator отображаются на дашбордах Grafana. Как получить доступ в Grafana написано [здесь](dostupy-k-komponentam-modulya.md).

После загрузки интерфейса Grafana вы увидите следующее окно:

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 184749.png" alt=""><figcaption><p>Стартовый дашборд</p></figcaption></figure>

Первый дашборд, который вам доступен после входа, называется General / Home. В левой части он показывает список избранных (Starred) дашбордов, в правой части - отображает текущий статус сервисов и баз данных Primo RPA Orchestrator.

Кликнув на имя интересующего вас дашборда в списке, система автоматически перейдет на него. В появившемся окне:

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 184831.png" alt=""><figcaption><p>Дашборд PROD / System Status</p></figcaption></figure>

вам можете в режиме чтения работать с дашбордом. На картинке выше отображается сводный статус системы Primo RPA Orchestrator, а так же основные показатели сервера (CPU, MEM, Disk, SWAP).

Если какой-либо из показателей подкрашен желтым или красным цветом - значит, что его функционирование нарушено.

На некоторых представлениях вы может изменить период, за который отображаются данные на дашборде. Сделать это можно с использованием меню time-picker в правой верхней части экрана:

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 184856.png" alt=""><figcaption><p>Time Picker</p></figcaption></figure>

Так же, возможно указать интервал автоматического обновления представления:

<figure><img src="../.gitbook/assets/Screenshot 2023-04-06 184913.png" alt=""><figcaption><p>Auto refresh period</p></figcaption></figure>

Более детальная информация, в том числе - описание дополнительных возможностей Grafana и настройка собственных дашбордов доступно в [официальной документации вендора по ссылке](https://grafana.com/docs/grafana/latest/dashboards/).
