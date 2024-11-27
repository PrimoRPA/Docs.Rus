---
description: Primo.AI server
---

# Сервер Primo.AI

![](<../../../.gitbook/assets1/windows_items/WFAttachPrimoAIServer.png>)

Контейнер, который производит подключение к сервису [Primo RPA AI Server](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/common). 

Чтобы отправлять запросы к подключенному серверу, поместите в контейнер элементы группы **AI > Умный OCR** или группы **AI > NLP**.

## Перед началом работы

Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server).


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Сервер** *[String]* — адрес сервера. Пример: `"https://ip:port/"`.
1. **Логин** *[String]* — логин пользователя.
1. **Пароль** *[String]* — пароль пользователя.
1. **Защищенный пароль** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0)]* — параметр для указания защищенного пароля.
3. **Тайм-аут** *[Int32]* — предельное время ожидания действий сервера, указывается в миллисекундах. По умолчанию `30000`. 
