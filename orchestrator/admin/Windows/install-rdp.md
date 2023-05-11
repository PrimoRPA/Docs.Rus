# Установка RDP
Приложение используется для поддержания активных RDP-сессий и может быть запущено в обычном режиме, с окном и в режиме скрытого окна. Обычно на том же сервере, что и Primo.WebApi.

Раздел содержит инструкцию по установке RDP под Windows 2016 Server. 

**Как установить RDP:**

1\. Архив `Distr\Windows\RDP.zip` из комплекта поставки нужно распаковать в папку `C:\Rimo\RDP`.\
2\. В файле `Primo.Orchestrator.RDP.exe.config` настраиваем:
* путь до файла с логом;

![](<../../../.gitbook/assets/install-rdp-1.png>)

* строку соединения с БД аналогично строке для БД **ltools** из конфигурационного файла WebApi (в том числе **dbVendor**); 
* фильтрацию адресов машин роботов (опционально) - в случае, если для каждого экземпляра приложения планируется использовать свой список адресов:

![](<../../../.gitbook/assets/install-rdp-2.png>)

3\. Приложение запускается из командной строки:
```
> cd c:\Primo\RDP
> Primo.Orchestrator.RDP --console --hidden
```
Без параметра `--hidden` приложение запустится с окном. Такой режим стоит использовать при установке и настройке Оркестратора. 

4\. Далее приложение нужно поместить в автозагрузку:

* Создаем bat-файл `C:\rdp_start.bat` со следующими командами: 
```
cd c:\Primo\RDP 
Primo.Orchestrator.RDP --console --hidden 
```
* Вносим созданный файл в автозагрузку Windows командой:
```
> REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v rdp_start /t REG_SZ /d "C:\rdp_start.bat"
```
* Отключаем запрос подтверждения сертификата при подключении к удаленному рабочему столу. Для этого в системный реестр в ветку
`HKEY_LOCAL_MACHINE/Software/Microsoft/Terminal Server Client` добавляем ключ **DWORD** с именем **AuthenticationLevelOverride** и значением **0**: 

![](<../../../.gitbook/assets/install-rdp-3.png>)

5\. Убедиться, что приложение работает, когда оно запущено в скрытом режиме, можно командой:
```
> tasklist /fi "Primo.Orchestrator.RDP.exe"
```

:white_check_mark: **Готово**: RDP успешно установлен под Windows 2016 Server.



