# Установка RabbitMQ 
Раздел содержит инструкцию по установке RabbitMQ под Windows 2016 Server. 

**Как установить RabbitMQ :**

1\. Разрешаем localhost в файле `C:\Windows\System32\drivers\etc\hosts`.

![](<../../../.gitbook/assets/install-rabbitmq-1.png>)

2\. Разархивируем папку rabbitmq.zip в туже папку C:\Install\rabbitmq
Сначала устанавливаем Erlang (otp_win64_23.2.exe), все параметры по умолчанию.
Затем устанавливаем сам RabbitMQ (rabbitmq-server-3.8.11.exe), все параметры по умолчанию. 
Производим первоначальное конфигурирование RabbitMQ

> cd C:\Program Files\RabbitMQ Server\rabbitmq_server-3.8.11\sbin
> rabbitmq-plugins.bat enable rabbitmq_management
> rabbitmqctl.bat add_user "admin" "Qwe123!@#" 
> rabbitmqctl.bat set_user_tags admin administrator 
> rabbitmqctl.bat set_permissions -p / admin ".*" ".*" ".*" 
> rabbitmqctl.bat stop
> rabbitmqctl.bat start_app

Открываем веб-интерфейс управления RabbitMQ на http://localhost:15672*, убеждаемся, что он открывается:

*\*Авторизоваться со встроенной учетной записью guest можно только если административная панель работает на localhost*.

![](<../../../.gitbook/assets/install-rabbitmq-2.png>)

Заходим под пользователем admin/Qwe123!@#:

![](<../../../.gitbook/assets/install-rabbitmq-3.png>)

Дальнейшее управление RabbitMQ можно осуществлять через этот веб-интерфейс.

:white_check_mark: **Готово**: RabbitMQ успешно установлен под Windows 2016 Server.



