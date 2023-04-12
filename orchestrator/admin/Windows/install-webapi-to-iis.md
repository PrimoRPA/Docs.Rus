# Установка WebApi и UI на IIS
Раздел содержит инструкцию по установке WebApi и UI на IIS под Windows 2016 Server. Перед выполнением инструкции требуется установить все последние обновления Windows.

## Включение компьютера в AD

:grey_exclamation: ***Не нужно, если используется DHCP***

1\. Перед установкой IIS настроим статический IP адрес и DNS. В DNS прописываем IP контроллера AD. Это нужно для включения компьютера в AD.\
Правой кнопкой мыши щелкаем по иконке **Network** в правом нижнем углу:

![](<../../../.gitbook/assets/install-webapi-ad-1.png>)

2\. Во всплывающем меню выбираем **Open Network and Sharing Center**:

![](<../../../.gitbook/assets/install-webapi-ad-2.png>)

3\. В открывшемся окне **Network and Sharing Center** в левом меню выбираем **Change adapter settings**:	

![](<../../../.gitbook/assets/install-webapi-ad-3.png>)

4\. В открывшемся окне **Network Connections** выбираем сетевой адаптер и щелкаем по нему правой кнопкой мыши:

![](<../../../.gitbook/assets/install-webapi-ad-4.png>)

5\. Во всплывающем меню выбираем **Properties**:

![](<../../../.gitbook/assets/install-webapi-ad-5.png>)

6\. В открывшемся окне **Ethernet Properties** кликаем по **Internet Protocol Version 4 (NCP/IPv4)**: 

![](<../../../.gitbook/assets/install-webapi-ad-6.png>)

7\. В открывшемся окне **Internet Protocol Version 4 (NCP/IPv4) Properties** настраиваем параметры:
* Выбираем **Use the following IP address** и прописываем значения полей **IP address**, **Subnet mask** и **Default gateway** (для VM значения этих полей можно узнать командой ipconfig);
* Выбираем **Use the following DNS server addresses** и прописываем в поле **Preferred DNS server** IP контроллера домена.

![](<../../../.gitbook/assets/install-webapi-ad-7.png>)

8\. Для удобства дальнейших настроек меняем имя компьютера, например, на **IIS**. В главном меню Windows выбираем пункт **Settings**:

![](<../../../.gitbook/assets/install-webapi-ad-8.png>)

9\. В открывшемся окне **Settings** выбираем пункт меню **System**:

![](<../../../.gitbook/assets/install-webapi-ad-9.png>)

10\. И потом **About**. При помощи кнопки **Rename PC** переименовываем компьютер, дожидаемся перезагрузки:

![](<../../../.gitbook/assets/install-webapi-ad-10.png>)

11\. Здесь же присоединяем компьютер к AD:

![](<../../../.gitbook/assets/install-webapi-ad-11.png>)

12\. Нажимаем кнопку **Join a domain** и выбираем имя AD:

![](<../../../.gitbook/assets/install-webapi-ad-12.png>)

13\. Нажимаем кнопку **Next** и вводим логин и пароль доменной учетной записи:

![](<../../../.gitbook/assets/install-webapi-ad-13.png>)

14\. Добавляем информацию о доменной учетной записи на компьютер, выбрав **Account type** = **Administrator**:

![](<../../../.gitbook/assets/install-webapi-ad-14.png>)

15\. Перезагружаем компьютер:

![](<../../../.gitbook/assets/install-webapi-ad-15.png>)

16\. После перезагрузки компьютера появится возможность входа в AD с доменной учетной записью:

![](<../../../.gitbook/assets/install-webapi-ad-16.png>)

## Установка IIS

![](<../../../.gitbook/assets/install-webapi-iis-1.png>)

![](<../../../.gitbook/assets/install-webapi-iis-2.png>)

![](<../../../.gitbook/assets/install-webapi-iis-3.png>)

![](<../../../.gitbook/assets/install-webapi-iis-4.png>)

![](<../../../.gitbook/assets/install-webapi-iis-5.png>)

![](<../../../.gitbook/assets/install-webapi-iis-6.png>)

![](<../../../.gitbook/assets/install-webapi-iis-7.png>)

![](<../../../.gitbook/assets/install-webapi-iis-8.png>)

![](<../../../.gitbook/assets/install-webapi-iis-9.png>)

![](<../../../.gitbook/assets/install-webapi-iis-10.png>)

![](<../../../.gitbook/assets/install-webapi-iis-11.png>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

:white_check_mark: **Готово**: приложение Nginx успешно установлено и добавлено в автозагрузку Windows.
