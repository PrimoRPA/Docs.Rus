# Настройка теневой RDP-сессии
Раздел содержит пошаговую инструкцию для настройки теневой RDP-сессии.

**Шаг 1:** Скопируйте скрипт для подключения теневой сессии `scr2.ps1` в папку `C:\Primo`.

**Шаг 2:** Для каждого сервера (машины робота), к которому планируется теневое подключение, необходимо настроить политику. Для этого запустите gpedit.msc, перейдите в Computer Configuration ➝ Administrative Templates ➝ Windows Components ➝ Remote Desktop Services ➝ Remote Desktop Session Host ➝ Connections и выберите **Set rules for remote control of Remote Desktop Service user sessions**:

![](<../../../.gitbook/assets/shadow-rdp-1.png>)

**Шаг 3:**	В окне управления правилами выберите те же настройки, как на скрине:

![](<../../../.gitbook/assets/shadow-rdp-2.png>)

**Шаг 4:** Нажмите **Apply**.

**Шаг 5:** Запустите PowerShell под администратором и выполните команду `gpupdate /force`.

**Шаг 6:** В PowerShell перейдите в папку `C:\Primo`, запустите скрипт `scr2.ps1` с параметрами `-UserName` и `-ServerName`:

![](<../../../.gitbook/assets/shadow-rdp-3.png>)

**Шаг 7:** Полный контроль сессии:

![](<../../../.gitbook/assets/shadow-rdp-4.png>)
