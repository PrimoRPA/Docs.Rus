# Настройки Prometheus Server

Конфигурация Prometheus Server описывается в файле **%mon\_home%\prometheus-server\prometheus.yml**

Файл **prometheus.yml** — это конфигурационный файл для сервера мониторинга Prometheus. Он содержит основные настройки, необходимые для сбора метрик и определения целей сбора данных.

Основные разделы файла **prometheus.yml** включают:

* **global**: раздел содержит глобальные настройки для Prometheus, такие как имя и версия, а также настройки времени жизни метрик и хранения данных.
* **scrape\_configs**: раздел определяет настройки для сбора метрик от конкретных экспортеров. В нем определяются конечные точки (endpoint) для сбора данных, параметры подключения, настройки времени сбора, а также лейблы, которые будут назначены метрикам. В этой секции указывается в том числе параметры мониторинга для [Prometheus Exporter Blackbox](konfiguraciya-modulya/prometheus-exporters.md#prometheus-exporter-blackbox)
* **rule\_files**: раздел, где определяются правила алертинга. Он содержит список файлов с правилами, которые определяют условия и параметры, при которых должно генерироваться оповещение.
* **alerting**: раздел, где определяются настройки для отправки оповещений. Он содержит настройки почты, webhook и другие.

#### Значения по умолчанию

{% code overflow="wrap" lineNumbers="true" %}
```yaml
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["127.0.0.1:9090"]


  - job_name: blackbox # To get metrics about the exporter itself
    metrics_path: /metrics
    static_configs:
      - targets:
        - 127.0.0.1:9115   # For Windows and macOS replace with - host.docker.internal:9115

  - job_name: blackbox-http # To get metrics about the exporter’s targets
    metrics_path: /probe
    params:
      module: [http_2xx]
    static_configs:
      - targets:
        - https://of-primo-orh:44392/ # Target to probe with http on port 8080
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: 127.0.0.1:9115  
        
        
  - job_name: blackbox-tcp # To get metrics about the exporter’s targets
    metrics_path: /probe
    params:
      module: [tcp_connect]
    static_configs:
      - labels:
          name: 'RDP 3389'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:3389  # Сервер приложений RDP  
      - labels:
          name: 'MachineInfo 5051'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:5051  # Сервер приложений MachineInfo
      - labels:
          name: 'Agent Robot 5002'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:5002  # Робот Агент
      - labels:
          name: 'WebAPI 5001'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:5001  # Сервер приложений WebAPI
      - labels:
          name: 'Front 44392'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:44392 # Сервер приложений Front
      - labels:
          name: 'Robot 1 8000'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:8000  # Робот 1
      - labels:
          name: 'AMPQ 5672'
          service: 'TCP доступность сервисов Primo'
        targets:
          - 127.0.0.1:5672  # Сервер приложений AMPQ

          
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: 127.0.0.1:9115  
        
  - job_name: rabbitmq
    honor_labels: true
    static_configs:
      - targets: ['127.0.0.1:15692']
        labels:
          instance: 'rabbitmq_primo'
          
  - job_name: wmi_exporter
    static_configs:
      - targets: ['127.0.0.1:9182']
      
  - job_name: odbc_exporter_ltools
    static_configs:
      - targets: ['localhost:9296']
        labels:
          alias: ltools
          
  - job_name: odbc_exporter_ltoolsidentity
    static_configs:
      - targets: ['localhost:9297']
        labels:
          alias: ltoolsidentity
          
  - job_name: odbc_exporter_ltoolslogs
    static_configs:
      - targets: ['localhost:9298']
        labels:
          alias: ltoolslogs
          
  - job_name: odbc_exporter_ltoolslicense
    static_configs:
      - targets: ['localhost:9299']
        labels:
          alias: ltoolslicense
```
{% endcode %}
