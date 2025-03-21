# Первичная настройка системы

После установки Idea Hub потребуется выполнить первичную настройку системы. По её завершении в Idea Hub появится информация об автоматизируемых бизнес-процессах и привязанной статистике из Оркестратора. 

Порядок действий:
1. Выполните [подключение к Оркестратору](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/initial-setup/connecting-to-orch), чтобы получать актуальные данные из БД.
1. В веб-интерфейсе Idea Hub [создайте контуры](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/initial-setup/environments) организации и синхронизируйте подключение к Оркестратору.	
1. Выполните [импорт данных](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/initial-setup/import):
   * **Без использования LDAP** — сформируйте файлы `users.xlsx`, `areas.xlsx`, `process.xlsx` для массового импорта пользователей, департаментов и процессов из Оркестратора. Загрузите указанные файлы в веб-интерфейсе Idea Hub.
   * **С использованием LDAP** — [подключитесь к LDAP](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/admin/modules/integration-ldap), чтобы автоматически импортировать пользователей и департаменты из Active Directory (AD). Сформируйте файл `process.xlsx`, предварительно вписав в колонки коды департаментов и пользователей, импортированных с помощью LDAP. Загрузите указанный файл в веб-интерфейсе Idea Hub.



