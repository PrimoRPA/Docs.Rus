---
description: 
---

# Сервер ContentCapture

![](<../../../.gitbook/assets1/windows_items/library/WFAttachContentAIServer-2.png>)

Контейнер, который подключает к серверу ContentCapture – платформе для интеллектуальной обработки информации из различных типов документов. 

## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет Primo.OCR.ContentAI, иначе данный элемент будет недоступен.


## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Сервер** *[String]* — URL адрес сервера. Пример: `"http://localhost/ContentCapture12/Server/API/v1/Soap"`.
1. **Таймаут\*** *[Int32]* — максимальное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `20000`.
1. **Аутентификация Windows** *[Boolean]* — определяет, следует ли использовать аутентификацию Windows. По умолчанию галочка установлена — аутентификация используется.
1. **Delegation** *[Boolean]* — определяет, следует ли использовать делегацию. По умолчанию галочка отсутствует — делегация не используется.
1. **Роль** — роль пользователя. Доступные значения:
   * `Processing Station` — значение по умолчанию.
   * `Scanning Operator`
   * `Data Verification Operator`
   * `Verification Operator`
   * `Senior Verification Operator`
   * `Processing Server`
   * `Project Settings Editor`
   * `Monitoring Operator`
   * `Administrator`
   * `External User`
   * `Web Capture Operator`
   * `Operators Manager`
   * `User Defined`
1. **Станция** — станция ContentCapture. Доступные значения:
   * `WT_External Station` — значение по умолчанию.
   * `WT_Scanning`
   * `WT_Verification`
   * `WT_Validation`
   * `WT_Processing Server`
   * `WT_Setup`
   * `WT_Processing Station`
   * `WT_Remote Data Verification`
   * `WT_Remote Verification`
   * `WT_Monitoring`
   * `WT_Front Office`
   * `WT_Web Validation`
   * `WT_Web Scanning`
1. **Логин** *[String]* — логин пользователя.
1. **Пароль** *[String]* — пароль пользователя.
1. **Защищенный пароль** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0)]* — поле для вставки защищенного пароля.

