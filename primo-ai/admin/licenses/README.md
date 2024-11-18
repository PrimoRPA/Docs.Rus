# Лицензии

Primo RPA AI Server — лицензированный сервис платформы Primo RPA. Лицензии запрашиваются у вендора на вкладке **Настройки > Лицензии**. Только пользователь пользователем с ролью [Administrator](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/system-users#vstroennye-roli) вправе запрашивать лицензии и управлять ими.

Лицензированию подлежат следующие части сервиса:
* Primo RPA AI Server — программные компоненты для машины сервера. 
* Агент Primo RPA AI Server — программный компонент для целевой машины, на которой будет работать [модель](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/glossary#model) OCR или NLP.

Для полноценной работы с сервисом необходимо запросить у вендора оба типа лицензий. Количество лицензий каждого типа определяется:
* Количеством [тенантов](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/common/access-control#tenanty) — для каждого тенанта требуется своя отдельная лицензия. Если вы планируете использовать только тенант по умолчанию, значит, вам будет достаточно одной лицензии с типом Primo RPA AI Server.
* Количеством одновременно работающих агентов — на одной целевой машине должен быть установлен только один агент. Свободная лицензия привязывается к агенту, к которому в первую очередь поступил запрос на инференс. Агент освобождает лицензию только после того, как администратор выключил целевую машину с агентом, удерживающим лицензию.

![](<../../../.gitbook/assets1/primo-ai/licenses.png>)

### Порядок получения лицензии 

1. [Сформируйте](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#zaprosit-licenziyu) текстовый запрос на лицензию.
1. Отправьте на электронную почту `License@primo-rpa.ru` файлы с запросом лицензий.
2. [Загрузите](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#dobavit-licenziyu) полученные от вендора лицензии. Убедитесь, что лицензии валидны.
3. Если вы используете несколько тенантов — [назначьте](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management#vydat-licenziyu-na-tenant) лицензии для каждого из тенантов. 

### См. также

* [Управление лицензиями](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/licenses/license-management)





