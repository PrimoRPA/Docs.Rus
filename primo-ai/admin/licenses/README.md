# Лицензии

Primo RPA AI Server — лицензированный сервис платформы Primo RPA. Лицензии запрашиваются на вкладке **Настройки > Лицензии**. Только пользователь пользователем с ролью [Administrator](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/system-users#vstroennye-roli) вправе запрашивать лицензии и управлять ими.

Лицензированию подлежат следующие части сервиса:
* **Primo RPA AI Server** — программные компоненты для машины сервера. 
* **Агент Primo RPA AI Server** — программный компонент для целевой машины, на которой будет работать [модель](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/glossary#model) OCR или LLM.

Для полноценной работы с сервисом необходимо запросить у вендора оба типа лицензий. Количество лицензий каждого типа определяется:
* Количеством [тенантов](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/common/access-control#tenanty) — для каждого тенанта требуется своя отдельная лицензия. Если вы планируете использовать только тенант по умолчанию, значит, вам будет достаточно одной лицензии с типом Primo RPA AI Server.
* Количеством одновременно работающих агентов — на одной целевой машине должен быть установлен только один агент. Включенная и доступная целевая машина по умолчанию будет пытаться удержать свободную лицензию. Агент освободит лицензию только после того, как администратор выключит целевую машину на странице **Настройки > Целевые машины**.

![](<../../../.gitbook/assets1/primo-ai/licenses.png>)

### Порядок получения лицензии 

1. [Сформируйте](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#zaprosit-licenziyu) текстовый запрос на лицензию.
1. Отправьте на электронную почту `License@primo-rpa.ru` файлы с запросом лицензий.
2. [Загрузите](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#dobavit-licenziyu) на сервер полученные от вендора лицензии. Убедитесь, что лицензии валидны.
3. Если вы используете несколько тенантов — [назначьте](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#vydat-licenziyu-na-tenant) лицензии для каждого из тенантов. 

### См. также

* [Управление лицензиями](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management)





