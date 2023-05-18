# Атрибуты безопасности

Конфигурационные файлы поставляются с зашифрованными паролями. Используется 4 предустановленных пароля - см. таблицу.

#### Таблица 1 – Предустановленные пароли.

|	Открытый пароль	| Зашифрованный пароль	| Назначение |
| --------------- | --------------------- | ---------- |
| Qwe123!@# | JLWIyl1xZNDVVx8tcVllOg== | ActiveDirectory, SslCert, RabbitMQ |
| postgres  | 49EqQ30zfcQTWxEGYE/mSw== | БД: ltools, ltoolsidentity, ltoolslicense, ltoolslogs (PostgeSQL) |
| 123!@#Qwe123!@#Qwe123 | 8TQ18jklcX3CPIsG6cVeb4iClxAxrqSabembVRUnvXQ= | Email, с которого происходит рассылка |
| sa | OrrNv0YQhLhnAwG+CuUPKA== | БД: ltools, ltoolsidentity, ltoolslicense, ltoolslogs (MS SQL SERVER) |

Если требуется сменить предустановленный пароль - например, у пользователя БД меняется пароль - то его нужно сначала зашифровать при помощи программы **LTools.Orchestrator.PasswordEncriptor.exe**\*:

\* *Архив PasswordEncriptor.zip из [комплекта поставки](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/kit).*

![](<../../.gitbook/assets/3.Шифрование паролей.png>)

После чего скопировать из окна терминала зашифрованные пароли (находятся под строкой **Copy following string:** ) в конфигурационные файлы `appsettings.ProdWin.json`\*\* и `appsettings.Worker.json`.

\*\* *Или в appsettings.ProdLinux.json, если поставка для Linux*.

Соль для алгоритма шифрования паролей находится в одной из обфусцированных dll Оркестратора, поэтому шифрование доступно только с помощью LTools.Orchestrator.PasswordEncriptor.exe.

Продолжительность сессии в минутах (время жизни токена) настраивается в файле `appsettings.ProdWin.json` в секции **Security:Jwt**. См. значение для параметра **SessionLifetimeMin**:

```json
 "Security": {
    "Jwt": {
      "Issuer": "LToolsOrchestratorWebApi",
      "Audience": "LToolsOrchestratorUi",
      "SigningKey": "0d5b3235a8b403c3dab9c3f4f65c07fcalskd234n1k41230",
      "SessionLifetimeMin": 720
    },
```
Сложность пароля (длина, обязательные символы, истории старых паролей и т.п.) настраивается в `appsettings.ProdWin.json` в секции **Security:Password**. Параметр **MaxOldPasswords** отвечает за максимальное количество старых паролей в истории (чтобы пользователь при смене пароля не мог использовать недавние значения).

```json
"Password": {
  "RequireDigit": true,
  "RequireLowercase": true,
  "RequireNonAlphanumeric": true,
  "RequireUppercase": true,
  "RequiredLength": 8,
  "RequiredUniqueChars": 1,
  "MaxOldPasswords": 5
},
```
В секции **Security:Lockout** настраиваются параметры блокировки пользователя при неуспешных попытках ввода пароля. К ним относятся время блокировки и максимальное количество неудачных попыток:

```json
"Lockout": {
  "DefaultLockoutTimeSpan": "00:01:00",
  "MaxFailedAccessAttempts": 5
}
```
В БД пароли для машин роботов хранятся в зашифрованном виде. Если по какой-то причине пароль не расшифровывается (например, если его неверно исправить в БД вручную), то при работе приложения в БД сохранится случайная зашифрованная строка. Работать такой пароль не будет, его необходимо исправить на правильный через UI Оркестратора.


