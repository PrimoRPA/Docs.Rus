---
description: Disconnect Database (SAP HANA)
---

# Отсоединиться от базы данных (SAP HANA)

  ![](<../../../.gitbook/assets1/disconnect_hana_sap.png>)


Компонент производит отсоединение от базы данных.

## Перед началом работы

Установите в Primo RPA Studio (Windows) пакет [Primo.Sap.Data.Hana](https://www.nuget.org/packages/Primo.Sap.Data.Hana), иначе данный элемент будет недоступен.  
Также необходимо предварительно установить клиент SAP HANA, который можно скачать с [официального сайта SAP HANA](https://tools.hana.ondemand.com/#hanatools).

## Свойства

Символом `*` отмечены обязательные для заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**База данных:**
1. *Соединение с БД\* *[Primo.Sap.Data.Hana.DatabaseInst] — экземпляр отсоединения с базой данных.
