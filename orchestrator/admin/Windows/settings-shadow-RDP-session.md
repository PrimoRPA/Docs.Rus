# Настройка теневой RDP-сессии

**Шаг 1:** Копируем скрипт для подключения теневой сессии scr2.ps1 в папку C:\Primo.

**Шаг 2:** Для каждого сервера (машины робота), к которому планируется теневое подключение необходимо настроить политику, запускаем gpedit.msc, переходим Computer Configuration -> Administrative Templates -> Windows Components -> Remote Desktop Services -> Remote Desktop Session Host -> Connections и выбираем Set rules for remote control of Remote Desktop Service user sessions
