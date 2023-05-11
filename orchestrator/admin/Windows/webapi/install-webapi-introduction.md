# Установка WebApi и UI на IIS
Раздел содержит инструкцию по установке WebApi и UI на IIS под Windows 2016 Server. Перед выполнением инструкции требуется установить все последние обновления Windows.

### Содержание

1. Включение компьютера в AD (пропустите, если используется DHCP).
2. [Установка IIS](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/webapi-install-iis.md).
3. [Разворачивание узлов веб-приложения](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/web-app-nodes.md).

## Включение компьютера в AD

:grey_exclamation: ***Не нужно, если используется DHCP***

1\. Перед установкой IIS настроим статический IP адрес и DNS. В DNS прописываем IP контроллера AD. Это нужно для включения компьютера в AD.\
Правой кнопкой мыши щелкаем по иконке **Network** в правом нижнем углу:

![](<../../../../.gitbook/assets/install-webapi-ad-1.png>)

2\. Во всплывающем меню выбираем **Open Network and Sharing Center**:

![](<../../../../.gitbook/assets/install-webapi-ad-2.png>)

3\. В открывшемся окне **Network and Sharing Center** в левом меню выбираем **Change adapter settings**:	

![](<../../../../.gitbook/assets/install-webapi-ad-3.png>)

4\. В открывшемся окне **Network Connections** выбираем сетевой адаптер и щелкаем по нему правой кнопкой мыши:

![](<../../../../.gitbook/assets/install-webapi-ad-4.png>)

5\. Во всплывающем меню выбираем **Properties**:

![](<../../../../.gitbook/assets/install-webapi-ad-5.png>)

✅ Готово: веб-сервер IIS успешно установлен в Windows 2016 Server. Для завершения установки WebApi и UI на IIS перейдите к разворачиванию узлов веб-приложения.

6\. В открывшемся окне **Ethernet Properties** кликаем по **Internet Protocol Version 4 (NCP/IPv4)**: 

![](<../../../../.gitbook/assets/install-webapi-ad-6.png>)

7\. В открывшемся окне **Internet Protocol Version 4 (NCP/IPv4) Properties** настраиваем параметры:
* Выбираем **Use the following IP address** и прописываем значения полей **IP address**, **Subnet mask** и **Default gateway** (для VM значения этих полей можно узнать командой ipconfig);
* Выбираем **Use the following DNS server addresses** и прописываем в поле **Preferred DNS server** IP контроллера домена.

![](<../../../../.gitbook/assets/install-webapi-ad-7.png>)

8\. Для удобства дальнейших настроек меняем имя компьютера, например, на **IIS**. В главном меню Windows выбираем пункт **Settings**:

![](<../../../../.gitbook/assets/install-webapi-ad-8.png>)

9\. В открывшемся окне **Settings** выбираем пункт меню **System**:

![](<../../../../.gitbook/assets/install-webapi-ad-9.png>)

10\. И потом **About**. При помощи кнопки **Rename PC** переименовываем компьютер, дожидаемся перезагрузки:

![](<../../../../.gitbook/assets/install-webapi-ad-10.png>)

11\. Здесь же присоединяем компьютер к AD - нажимаем кнопку **Join a domain**:

![](<../../../.gitbook/assets/install-webapi-ad-11.png>)

12\. И выбираем имя AD, после чего жмем **Next**:

![](<../../../../.gitbook/assets/install-webapi-ad-12.png>)

13\. Вводим логин и пароль доменной учетной записи:

![](<../../../../.gitbook/assets/install-webapi-ad-13.png>)

14\. Добавляем информацию о доменной учетной записи на компьютер, выбрав в параметре **Account type** значение **Administrator**:

![](<../../../../.gitbook/assets/install-webapi-ad-14.png>)

15\. Перезагружаем компьютер:

![](<../../../../.gitbook/assets/install-webapi-ad-15.png>)

16\. После перезагрузки компьютера появится возможность входа в AD с доменной учетной записью:

![](<../../../../.gitbook/assets/install-webapi-ad-16.png>)

:white_check_mark: **Готово**: компьютер успешно включен в службу каталогов Active Directory. **Переходите к [установке IIS](https://github.com/PrimoRPA/Docs.Rus/blob/139-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%B8%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B0%D0%B4%D0%BC%D0%B8%D0%BD%D0%B0-%D0%B2-%D1%80%D0%B0%D0%B7%D0%B4%D0%B5%D0%BB-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0/orchestrator/admin/Windows/webapi/webapi-install-iis.md)**.



