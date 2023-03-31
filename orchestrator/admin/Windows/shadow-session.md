# Настройка теневой сессии
Раздел содержит пошаговую инструкцию для настройки теневой сессии.

**Шаг 1:** Скопируйте скрипт для подключения теневой сессии `scr2.ps1` в папку `C:\Primo`.

**Шаг 2:** Для каждого сервера (машины робота), к которому планируется теневое подключение, необходимо настроить политику. Для этого запустите gpedit.msc, перейдите в Computer Configuration ➝ Administrative Templates ➝ Windows Components ➝ Remote Desktop Services ➝ Remote Desktop Session Host ➝ Connections и выберите **Set rules for remote control of Remote Desktop Service user sessions**:

![](<../../../.gitbook/assets/shadow-rdp-1.png>)
