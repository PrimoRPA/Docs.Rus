# Расположение

Все компоненты модуля по умолчанию устанавливаются в домашний каталог Primo RPA Orchestrator. Значения по-умолчанию (aka %mon\_home%) для операционных систем:

| **Windows Server** | C:\Primo\monitoring\\  |
| ------------------ | ---------------------- |
| **RPM\DEB Linux**  | /opt/Primo/monitoring/ |

Прямые директории установленных по-умолчанию компонент модуля:

| [**Grafana**](konfiguraciya-modulya/nastroiki-grafana-server.md)                                               | [%mon\_home%\grafana](konfiguraciya-modulya/nastroiki-grafana-server.md)                                               |
| -------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Grafana Loki**                                                                                               | %mon\_home%\loki                                                                                                       |
| [**Prometheus Blackbox Exporter**](konfiguraciya-modulya/prometheus-exporters.md#prometheus-exporter-blackbox) | [%mon\_home%\prometheus-exporter-blackbox](konfiguraciya-modulya/prometheus-exporters.md#prometheus-exporter-blackbox) |
| [**Prometheus WMI Exporter**](konfiguraciya-modulya/prometheus-exporters.md#prometheus-exporter-wmi)           | [%mon\_home%\prometheus-exporter-wmi](konfiguraciya-modulya/prometheus-exporters.md#prometheus-exporter-wmi)           |
| [**Prometheus ODBC Exporter**](konfiguraciya-modulya/prometheus-exporters.md#prometheus-odbc-exporter)         | [%mon\_home%\prometheus-odbc-exporter](konfiguraciya-modulya/prometheus-exporters.md#prometheus-odbc-exporter)         |
| [**Prometheus Server**](nastroiki-prometheus-server.md)                                                        | [%mon\_home%\prometheus-server](nastroiki-prometheus-server.md)                                                        |
| **Python 3.11**                                                                                                | %mon\_home%\Python311                                                                                                  |

