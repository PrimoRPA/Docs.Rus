# Варианты развертывания компонентов

Возможные варианты развертывания компонентов Оркестратора из дистрибутивов приведены в таблице ниже. Варианты, для которых поддержка кластера не гарантирована производителем, выделены символом `*`.

| Компоненты | Windows | Linux |
| ---------- | ------- | ----- |
| MSSQL      | +       |   |
| PostgreSQL | `*`      | + |
| WebApi     | +       | + |
| States     | +       | + |
| Notifications | +    | + |
| Front      | +       | + |
| RobotLogs  | +       | + |
| RabbitMQ   | +       | + |
| RDP2       | +       | + |
| MachineInfo | +      | + |
| LogEventsWebhook | + | + |
| NuGet      | +       | + |


## Windows

Для Windows-серверов рекомендуется: MSSQL, WebApi (IIS), Front (IIS).

| Компоненты | Отдельная служба | Nginx   | IIS   |
| ------  | ---------------- | ------- | ----- |
| WebApi  |  +               |         | +     |
| Front   |                  | `*` (консольное приложение в автозагрузке) | + |
| RobotLogs | +              |         |       |
| MachineInfo |  +           |         |       |
| LogEventsWebhook | +       |         |       |
| NuGet   |  +               |         |       |

## Linux

Для Linux-серверов рекомендуется PostgreSQL\*.

\**Иначе не получится полноценно использовать pgbouncer. Не рекомендуется использовать PostgreSQL под Windows.*

| Компоненты   | Отдельная служба | Nginx   | IIS   |
| ------  | ---------------- | ------- | ----- |
| WebApi  |  +               |         |       |
| Front   |  +               | +       |       |
| RobotLogs | +              |         |       |
| MachineInfo |  +           |         |       |
| LogEventsWebhook | +       |         |       |
| NuGet   |  +               |         |       |
