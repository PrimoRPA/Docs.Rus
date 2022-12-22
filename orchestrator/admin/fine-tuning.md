# Тонкая настройка

## Внешняя поддержка RDP-сессии

Когда Роботу для работы требуется внешняя поддержка RDP-сессии, Оркестратор перед запуском Робота запрашивает открытие сессии в сервисе RDP. 

Процесс открытия RDP-сессии занимает некоторое время. Параметры открытия RDP-сессии настраиваются в секции 
**RobotStart.AttemptsKeepRDPSessionLevels**:

```json
"RobotStart": {
    "StartWithTracking": true,
    "TimeOutInMinutesForUnlock": 5,
    "IntevalForReleaseInSeconds": 300,
    "UseAgentLock": false,
    "AttemptsKeepRDPSessionLevels": [
      {
        "AttempCount": 3,
        "AttempExpirationInSeconds": 3
      },
      {
        "AttempCount": 3,
        "AttempExpirationInSeconds": 5
      },
      {
        "AttempCount": 3,
        "AttempExpirationInSeconds": 10
      }
    ]
  },
```
В таблице ниже приведено описание параметров открытия RDP-сессии:

| Параметр | Назначение | Примечание | 
| -------- | ---------- | ---------- |
| AttemptsKeepRDPSessionLevels | Массив пар параметров AttempCount и AttempExpirationInSeconds – уровней стратегии открытия RDP-сессии. Каждый последующий уровень должен иметь большее значение AttempExpirationInSeconds, чем предыдущий | Попытки открыть начинаются с уровня 0 (первый элемент массива). При исчерпании количества попыток происходит переход на следующий уровень, пока уровни не закончатся. Не рекомендуется использовать больше 3-х уровней |
| AttempCount | Количество попыток открытия RDP-сессии в рамках уровня |      |
| AttempExpirationInSeconds | Время задержки (сек) между попытками | Не гарантировано - при наличии многих RDP-пользователей время задержки может отличаться от указанного в настройке |



