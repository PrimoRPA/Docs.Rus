 # Лицензии

Лицензируются следующие продукты Primo RPA:
* Primo RPA Orchestrator (также Orchestrator, Оркестратор);
* Primo RPA Studio (также Studio, Студия);
* Primo RPA Robot (также Robot, Робот);
* Primo RPA Idea Hub (также Idea Hub).

В файле лицензии наименование продукта указано в теге `<product>`. Далее в статье оно обозначается как «мнемоника».

## Primo RPA Orchestrator

Для решения Primo RPA Orchestrator предоставляются лицензии:
1. **Orchestrator** — для работы в продуктивной среде. Лицензия запрашивается и обновляется через UI Оркестратора, хранится в БД Оркестратора. Процедура получения лицензии описана [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/licensing/new-license). Мнемоника — **orchestrator**.
2. **Orchestrator Non-Production** — для работы в непродуктивной среде (тестирования). Для запроса этой лицензии напишите вендору на [license@primo-rpa.ru](mailto:License@primo-rpa.ru). Мнемоника — **orchestrator**.


## Primo RPA Studio

Приложение Primo RPA Studio поставляется в двух [изданиях](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/common/editions):
* Community — ознакомительная версия, имеет ограничения и не подлежит лицензированию.
* Enterprise — полная версия, подлежит лицензированию.

Для издания Primo RPA Studio Enterprise предоставляются лицензии:

1. **Локальная лицензия** — предназначена для организаций с незначительным количеством роботов, или если Робот установлен на машине, которая не привязана к Оркестратору. Лицензия запрашивается, обновляется и хранится локально. Привязывается к учетной записи пользователя, таким образом, отсутствует возможность использовать ее на разных машинах. Подробнее о том, как получить локальную лицензию, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/enterprise#lokalnaya-licenziya). Мнемоника — **studio**. 
2. **Оркестраторная лицензия** — предназначена для организаций с большим количеством роботов, когда удобнее управлять лицензиями на разные продукты Primo RPA централизованно. Оркестраторная лицензия [запрашивается](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/licensing/new-license) и обновляется через UI Оркестратора, хранится в БД. Мнемоника — **studio**. 

   При запуске Primo RPA Studio Enterprise запрашивает свободную лицензию у Оркестратора. Если она имеется, то предоставляет пользователю возможность работы. При этом оркестраторную лицензию могут использовать Студии, развернутые на разных машинах. Например, одну лицензию до полудня можно запросить на одной машине, а после полудня — на другой. Одновременно использовать ее невозможно. 

## Primo RPA Robot

Для работы Primo RPA Robot требуется одна из ниже перечисленных лицензий.

### 1. Лицензия Robot (Enterprise)

Мнемоника — **robot**. Предназначена для Робота, работающего с Оркестратором в продуктивной среде (unattended-робот). Лицензия запрашивается [через Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/licensing/new-license), у которого тоже должна быть лицензия.

**Особенности работы по лицензии Robot (Enterprise)**:
* Обеспечивается автоматическая поддержка RDP-сессий для RDP-пользователей машины робота.
* Свободную действующую лицензию может использовать как Робот, развернутый на специальной машине и управляемый из Оркестратора, так и Робот, установленный локально на рабочем месте пользователя.


### 2. Лицензия Robot (Desktop)

Мнемоника — **robot_desktop**. Предназначена для Робота, работающего без Оркестратора в продуктивной среде (attended-робот). Робот должен быть установлен на рабочем месте пользователя и выступает в роли его цифрового помощника. 

**Особенности работы по лицензии Robot (Desktop)**:
*  Недоступна внешняя поддержка рабочего стола через RDP-соединение.
*  Недоступна работа с [аргументами проекта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/tasks-overview/tasks-arguments). 

Лицензию **Robot (Desktop)** возможно запросить двумя способами:
1. [Локально с машины пользователя, где запускается Робот](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation/registration-desktop). В этом случае лицензия запрашивается через утилиту Primo Robot RPA Runner, которая поставляется совместно с дистрибутивами Primo RPA Studio и Primo RPA Robot. Если лицензия запрошена локально с компьютера пользователя, то она будет привязана только к его учетной записи и компьютеру. На другой машине использовать лицензию не получится.
2. [Через Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/licensing/new-license) (требуется лицензия на Оркестратор). В этом случае полученная лицензия хранится в Оркестраторе, и ее могут использовать роботы, установленные на разных пользовательских машинах. Например, одну лицензию до полудня можно запросить на одной машине, а после — на другой. Одновременно использовать лицензию невозможно. 

### 3. Лицензия Robot (Enterprise) Non-Production

Предназначена для использования Робота в непродуктивной среде (тестирования). Для запроса этой лицензии напишите вендору на [license@primo-rpa.ru](mailto:License@primo-rpa.ru).

## Primo RPA Idea Hub

Для запроса лицензий на решение [Primo RPA Idea Hub](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/description) напишите вендору на [license@primo-rpa.ru](mailto:License@primo-rpa.ru).

