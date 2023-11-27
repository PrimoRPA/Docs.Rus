# Добавить машину

Перейдите в раздел **Машины** и следуйте инструкции ниже.

![](../.gitbook/assets1/add_mashine.png)  

1. **Добавление новой машины**:
   - Нажимаем кнопку **Добавить машину**.
   - Называем машину (например, Vicktor) и проверяем её доступность в сети.

3. **Обновление статуса машины**:
   - Нажимаем **Обновить** для проверки статуса. Если машина недоступна, это может быть связано с отсутствием установленного Агента.
   - Также рекомендуем предварительно ознакомиться с «Руководством по настройке машины Робота.docx» из комплекта поставки.

![](../.gitbook/assets1/add_maschine.png)

4. **Установка Агента**:
   - Переходим на машину, где будет установлен Агент.
   - Копируем в папку на машине два архива: `Agent` и `AgentInstaller`.
   - Создаем папку в корне диска **C** с названием **Primo**.
   - Распаковываем архивы агента в папку **Primo**.

5. **Настройка Агента**:
   - Обращаемся к документации по установке Агента.
   - Если PowerShell не установлен, сначала устанавливаем его.
   - Возвращаемся в папку с AgentInstaller и продолжаем установку, следуя указаниям из [видео](https://youtu.be/SlxgjXDrvsM?t=599)
   - Откройте PowerShell и вставьте следующий скрипт, чтобы создать переменную окружения для продуктивной среды:

   ```powershell
   [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
   ```

   - В PowerShell вставьте следующий скрипт для создания службы Агента. Этот скрипт устанавливает имя службы, путь к исполняемому файлу, описание и тип запуска:

   ```powershell
   New-Service -Name "Primo.Orchestrator.Agent" -BinaryPathName "C:\Primo\Agent\Primo.Orchestrator.Agent.exe" -Description "Primo.Orchestrator.Agent" -DisplayName "Primo.Orchestrator.Agent" -StartupType Automatic
   ```


6. **Конфигурация и запуск**:
   - Конфигурируем файл **appsettings.prod.json**, указывая текущий адрес Оркестратора.
   - Сохраняем изменения в файле.
   - Добавляем необходимые порты в фаервол, копируя и вставляя последовательно скрипты в PowerShell.
  
   ```powershell
   New-NetFirewallRule -Name "Primo Agent (5002)" -DisplayName "Primo Agent (5002)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 5002
   ```

   ```powershell
   New-NetFirewallRule -Name "Primo Robot (8000-9000)" -DisplayName "Primo Robot (8000-9000)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 8000-9000
   ```
   - Эти скрипты добавят исключения в фаервол, разрешая доступ к указанным портам.
   - Запускаем сервис агента.



8. **Проверка подключения и завершение настройки**:
   - Открываем браузер и проверяем, подключилась ли машина к Оркестратору.
   - Создаем задачу для удержания RDP-сессии, копируя файл `console.bat` в корень диска `C` из комплекта поставки Оркестратора.
   - Импортируем задачу с именем RDP Disconnector из пакета поставки Оркестратора в Task Viewer.

Теперь настройка машины полностью завершена. Если у вас возникли какие-либо трудности, ознакомьтесь с [видеоинструкцией](https://youtu.be/SlxgjXDrvsM?t=599).
