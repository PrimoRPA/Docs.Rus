---
description: Connect DataBase (SAP HANA)
---

# Присоединиться к БД (SAP HANA)


![](<../../../.gitbook/assets1/connect_sap_hana.png.png>)

Элемент производит подключение к базе данных.

## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет [Primo.Sap.Data.Hana](https://www.nuget.org/packages/Primo.Sap.Data.Hana), иначе данный элемент будет недоступен.  
Также необходимо предварительно установить клиент SAP HANA, который можно скачать с [официального сайта SAP HANA](https://tools.hana.ondemand.com/#hanatools).

## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**База данных:**
1. **Строка соединения\*** *[String]* — строка соединения с базой данных SAP HANA. Пример:  
`SERVER=<hostname>:<port>; DATABASE=<database name>; UID=<username>; PWD=<password>`.  

**Вывод:**
1. **Соединение с БД** *[Primo.Sap.Data.Hana.DatabaseInst]* — экземпляр соединения с базой данных.

