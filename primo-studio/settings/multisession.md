# Мультисессионная работа

При работе в многосессионном окружении, возможны ситуации, когда используемые Студиями порты пересекаются между разными пользователями. Для того, чтобы перенастроить порты, необходимо отредактировать файлы конфигураций приложений, входящих в состав дистрибутива:

| Primo.Studio.exe.config | Primo.Robot.x64.exe.config | Primo.Robot.exe.config | LTools.WebBrowser.Native.exe.config | LTools.Selector.exe.config |
| ----------------------- | -------------------------- | ---------------------- | ----------------------------------- | -------------------------- |
| debugPort               | debugPortStudio            | debugPortStudio        | -                                   | -                          |
| debugPortRobot          | debugPort                  | debugPort              | -                                   | -                          |
| selectorPort            | -                          | -                      | -                                   | selectorPort               |
| selectorPortStudio      | -                          | -                      | -                                   | selectorPortStudio         |
| webExtPort              | webExtPort                 | webExtPort             | webExtPort                          | webExtPort                 |
| webExtPortDebug         | webExtPortDebug            | webExtPortDebug        | webExtPortDebug                     | webExtPortDebug            |

**Обратите внимание на конфигурирование параметров связки Студия=Робот debugPort=debugPortStudio, debugPortRobot=debugPort**
