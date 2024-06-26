# Настройка машины робота

Руководство описывает настройку машины робота на Windows 2016 Server и предназначено для системных администраторов, имеющих навыки:

1. **Обязательно – уверенный пользователь ОС Windows**:
   * Владеть Проводником Windows для перемещения по папкам и файлам.
   * Создавать и редактировать текстовые файлы.
   * Копировать файлы, копировать текст из файлов, сохранять файлы.
2. **Обязательно – опыт администрирования ОС Windows**:
   * Уметь запускать программы из-под Администратора.
   * Иметь опыт работы в cmd.
   * Иметь опыт работы в PowerSchell.

## Введение

Компоненты Оркестратора (выборочно) и их связи и с роботами/машиной робота приведены на схеме ниже:

![](<../../../../.gitbook/assets/Машина-Робота-W. Компоненты Орка.png>)

Полная схема приведена в разделе [Компоненты системы](https://docs.primo-rpa.ru/primo-rpa/orchestrator/system-components).

**Агент** – self-hosted веб-приложение. Агент выполнен как .NET Core 3.1-приложение. Агент используется для развертывания и управления роботом на машине робота.

**Робот** – приложение, которое посредством Оркестратора развертывается на специальным образом настроенной машине и выполняет RPA-проект, который формируется заранее в Студии. На одной машине может работать несколько роботов. Все машины роботов должны быть настроены одинаково (версии ОС могут отличаться) и на каждой машине робота должен быть развернут Агент. Машин роботов может быть много.

**Порты**, указанные на схеме выше, далее используются при настройке конфигурационных файлов компонентов Агента, машин роботов и открытия портов на файерволе Windows (в том числе аппаратном в сети организации). Должно быть разрешено управление машиной робота по RDP.

Для настройки машины робота рекомендуется использовать чистую машину с Windows Server 2016 Standard x64, обязательно с последними обновлениями. На нее должна быть скопирована папка с комплектом поставки (см. выше подраздел **Файлы из комплекта поставки**). Это может быть любая папка - для определенности пусть будет папка `C:\Install`, поскольку в скрипте `PrimoWorker.ps1` прописана именно она.

Для выполнения команд и скриптов cmd и PowerShell должны запускаться из-под Администратора.



## Аппаратные требования

Для машины робота требуется рабочая станция под управлением Windows Server 2016 Standard x64, которая соответствует требованиям:

* **CPU** - 8 ядер
* **RAM** - 8 Гб
* **HDD** - 250 Гб (OS + Data)

Аппаратные требования зависят от количества одновременно работающих Роботов и задач, которые выполняют роботы. Рекомендуется по 1 ядру CPU на каждого робота.



## Файлы из комплекта поставки Оркестратора

Для настройки машины робота потребуются следующие файлы из [комплекта поставки](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/kit) Оркестратора:

|             Файл             |                             Описание                            |                               Примечание                              |
| :--------------------------: | :-------------------------------------------------------------: | :-------------------------------------------------------------------: |
|      AgentInstaller.zip      |                  Инсталлятор для машины робота                  | Должен использоваться как основной инструмент настройки машины робота |
|           Agent.zip          |                        Дистрибутив Агента                       |              Для настройки машины робота без инсталлятора             |
| PowerShell-7.1.3-win-x64.msi |                      Установщик PowerShell                      |              Для настройки машины робота без инсталлятора             |
|  ChromeStandaloneSetup64.exe |                    Установщик браузера Chrome                   |              Для настройки машины робота без инсталлятора             |
|        PrimoWorker.ps1       |          PowerSchell-скрипт для настройки машины робота         |              Для настройки машины робота без инсталлятора             |
|     restore\_console.bat     |               Скрипт перевода RDP-сессии в консоль              |              Для настройки машины робота без инсталлятора             |
|     RDP-Disconnector.xml     |          Windows Task, запускающий restore\_console.bat         |              Для настройки машины робота без инсталлятора             |
|     PasswordEncryptor.zip    | Программа шифрования паролей для конфигурационных файлов Агента |                                   -                                   |

Остальное ПО должно быть предустановлено в Windows.

## Установка Агента

Установить Агента Оркестратора на машине робота можно двумя способами:

* [из инсталлятора `AgentInstaller.zip`](https://docs.primo-rpa.ru/primo-rpa/orchestrator/setting-up-machines/windows/agentinstaller) - это основной инструмент для настройки машины робота;
* [без использования инсталлятора](https://docs.primo-rpa.ru/primo-rpa/orchestrator/setting-up-machines/windows/appendix) - альтернативный вариант на случай, если не получилось установить Агента через инсталлятор.
