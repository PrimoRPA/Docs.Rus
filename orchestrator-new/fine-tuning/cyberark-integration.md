# Интеграция с CyberArk

Интеграция с CyberArk используется для возможности хранить логин/пароль в ассетах типа Credentials отдельно от Оркестратора в CyberArk.
Параметры для настройки расположены в секции `CyberArk` конфигурационного файла WebApi:

![](../../../orchestrator-new/resources/fine-tuning/cyberark-integration.PNG)

Параметры:

1. **LogonType = 0** - зарезервировано, не меняется. 
2. **BaseUrl** – url CyberArk. 
3. **UserName** и **Password** – логин и пароль для авторизации в API CyberArk (должны предоставляться администратором CyberArk). Password должен быть зашифрован утилитой для шифрования паролей LTools.Orchestrator.PasswordEncryptor.
