# Активировать вкладку браузера

*Eng: Activate tab*

![](<../../../.gitbook/assets1/activatetab.png>)

Элемент предназначен для активации указанной вкладки браузера. Он работает корректно в следующих случаях:
- Внутри контейнеров «Открыть браузер» и «Присоединиться к браузеру».
- Через переменную, ссылающуюся на браузер.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство                | Тип                             | Описание                                                                                                                                                         |
|-------------------------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|**Браузер**         |                                                 |
| ID вкладки              | Int32                           | Идентификатор вкладки, которую нужно активировать.                                                                                                               |
| URL                     | String                          | URL страницы, которая должна быть активирована.                                                                                                                  |
| Заголовок вкладки       | String                          | Заголовок вкладки, которую нужно активировать. Можно использовать символ `*` в конце строки для частичного соответствия.                                         |
| Индекс вкладки          | Int32                           | Индекс вкладки, которую нужно активировать. Начинается с 0.                                                                                                      |
| Переменная              | LTools.WebBrowser.BrowserInst   | Переменная для сохранения ссылки на подключенный браузер.                                                                                                        |
|**Общие**             |     |                                                                                        |
| Наименование            | String    | Задает наименование активной вкладки.                                                            |
| Отключить логирование    | Boolean   | Опция отключения логирования при выполнении действия.                                            |
| Пауза до (мс)           | Integer   | Пауза перед выполнением действия, в миллисекундах.                                               |
| Пауза после (мс)        | Integer                       | Пауза после выполнения действия, в миллисекундах.                                                                                                                |
| Продолжить при ошибке    | Boolean                       | Указывает, должен ли процесс продолжаться при возникновении ошибки.                                                                                               |
| Скриншот завершения      | Boolean                       | Опция для создания скриншота по завершении действия.                                                                                                             |
| Скриншот ошибки          | Boolean                       | Опция для создания скриншота при возникновении ошибки.                                                                                                            

