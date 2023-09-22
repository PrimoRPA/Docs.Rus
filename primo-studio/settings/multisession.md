# Мультисессионная работа

При работе в многосессионном окружении возможны ситуации, когда используемые Студиями порты пересекаются между разными пользователями. Для того, чтобы перенастроить порты, необходимо отредактировать файлы конфигураций приложений, входящих в состав дистрибутива:

<table><thead><tr><th>Primo.Studio.exe.config</th><th>Primo.Robot.x64.exe.config</th><th>Primo.Robot.exe.config</th><th width="200">LTools.WebBrowser.Native.exe.config</th><th>LTools.Selector.exe.config</th></tr></thead><tbody><tr><td>debugPort</td><td>debugPortStudio</td><td>debugPortStudio</td><td>-</td><td>-</td></tr><tr><td>debugPortRobot</td><td>debugPort</td><td>debugPort</td><td>-</td><td>-</td></tr><tr><td>selectorPort</td><td>-</td><td>-</td><td>-</td><td>selectorPort</td></tr><tr><td>selectorPortStudio</td><td>-</td><td>-</td><td>-</td><td>selectorPortStudio</td></tr><tr><td>webExtPort</td><td>webExtPort</td><td>webExtPort</td><td>webExtPort</td><td>webExtPort</td></tr><tr><td>webExtPortDebug</td><td>webExtPortDebug</td><td>webExtPortDebug</td><td>webExtPortDebug</td><td>webExtPortDebug</td></tr></tbody></table>

**Обратите внимание на конфигурирование параметров связки Студия=Робот debugPort=debugPortStudio, debugPortRobot=debugPort**
