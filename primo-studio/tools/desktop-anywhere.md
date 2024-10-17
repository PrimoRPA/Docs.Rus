---
description: Primo Remote Agent (Desktop Anywhere)
---

# Desktop Anywhere

Это режим работы агента, который позволяет взаимодействовать с приложенияеми, запущенными на удаленной машине, используя протокол HTTP/HTTPS.

Для работы с удаленным приложением необходимо установить агента ***Primo Remote Agent** на удаленной машине.

Системные требования для установки и работы **Primo Remote Agent**:
- *Microsoft Windows 10* и выше или *Microsoft Windows Server 2016* и выше
- Клиент *RDP* от Microsoft
- *.NET Framework 4.6.1*
- *PowerShell*

Для работы в режиме **Desktop Anywhere** необходимо:
   - Открыть порт на удаленной машине и прописать его в файле *Primo.RemoteAgent.exe.config* в разделе `<add baseaddress=”...>`.
   - Указать логин и пароль в соответствующих разделах `<add key=”login”>, <add key=”pass”>` файла конфигурации.
   - Запустить агента с параметрами: `Primo.RemoteAgent.exe shownotify anywhere`.
   - Чтобы взаимодействовать с компонентами приложений удаленного рабочего стола в Студии в свойствах элемента [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach) выберите тип автоматизации **Desktop Anywhere** и укажите адрес, логин и пароль из файла конфигурации.


![](../../.gitbook/assets1/desk-anywhere-type.png)


## Где найти

Скачать архив *Primo Remote.Agent* и ознакомиться с видеоинструкцией можно по ссылке: [Primo Remote.Agent](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2fMisc%2fDesktop%20Anywhere#/).
