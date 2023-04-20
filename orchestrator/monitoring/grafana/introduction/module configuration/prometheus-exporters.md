# Prometheus Exporters

## Prometheus odbc exporter

Prometheus-odbc-exporter - это экспортер (компонент системы мониторинга) для Prometheus, который позволяет собирать метрики из баз данных, доступных через ODBC (Open Database Connectivity).

ODBC - это стандартный интерфейс доступа к различным типам баз данных. Prometheus-odbc-exporter позволяет подключиться к базам данных, используя ODBC-драйвер, и собирать метрики из них для мониторинга и анализа в Prometheus.

Использование экспортера зависит от типа инсталляции Primo RPA Orchestrator:

1. Если база данных Primo RPA Orchestrator - выделенная, то есть вся СУБД отдана под задачи Primo - экспортер контролирует БД по всем доступных ему параметрам;
2. Если базы Primo созданы на внешней СУБД и доступ к ней ограничен (например, БД Primo расположена рядом с вашими продуктивными базами) - проверяется только возможность чтения из таблиц БД Primo.Orchestrator, а мониторинг самой СУБД вы выполняет собственными средствами мониторинга.

Конфигурация **Prometheus ODBC Exporter** описывается в файле **%mon\_home%\prometheus-odbc-exporter\\%db\_name%\\**exporter.cfg, где **%db\_name%** - имя одной из 4-х баз Primo Orchestrator (ltools, ltoolsidentity, ltoolslicense и ltoolslogs).

```shell
# Queries are defined in sections beginning with 'query_'.
# Characters following this prefix will be used as a prefix for all metrics
# generated for the query.
# Result columns listed in QueryValueColumns will be exported as metrics, while any
# other columns will be used a labels.

[query_machbase_heap_blks_read]
QueryIntervalSecs = 30
QueryStatement = select count(*) as cnt from information_schema.tables
QueryValueColumns = cnt

```

## Prometheus Exporter WMI&#x20;

Prometheus Exporter WMI (Windows Management Instrumentation) - это экспортер, который позволяет собирать метрики с систем на операционной системе Windows и экспортировать их в формате, который может быть собран и использован Prometheus для мониторинга и анализа.

WMI - это технология, которая позволяет получать информацию о системе и ее компонентах на устройствах под управлением Windows. Экспортер WMI использует эту технологию для извлечения метрик, таких как загрузка процессора, использование памяти и дискового пространства, а также информации о сетевых интерфейсах и т.д.

Экспортер WMI работает как прослойка между системой и Prometheus, собирая метрики из WMI и преобразуя их в формат, который может быть собран Prometheus. Это позволяет использовать метрики, собранные с систем Windows, в Prometheus для мониторинга и анализа, что помогает улучшить производительность и надежность системы.

По-умолчанию, экспортер запускается как сервис WinOS с параметрами "cpu,cpu\_info,cs,iis,logical\_disk,memory,mssql,net,os,process,service,system,time,terminal\_services". В таком режиме экспортер собирает данные о:

* **cpu**: процент использования процессора по ядрам, время работы в user- и kernel-режимах, количество прерываний;
* **cpu\_info**: информация о процессоре (название, количество ядер, частота);
* **cs**: информация о контекстных переключениях (количество переключений за секунду);
* **iis**: информация о работе IIS (Internet Information Services) (количество запросов в секунду, время ответа сервера, количество обрабатываемых запросов);
* **logical\_disk**: информация о логических дисках (количество свободного места, общий размер диска);
* **memory**: информация об использовании памяти (количество свободной и используемой памяти, количество страниц памяти);
* **mssql**: информация о работе MS SQL Server (количество запросов, время выполнения запросов);
* **net**: информация о сетевых интерфейсах (количество переданных и полученных пакетов, скорость передачи данных);
* **os**: информация об операционной системе (тип, версия, количество процессоров);
* **process**: информация о процессах (ID, использование памяти, количество потоков);
* **service**: информация о службах Windows - статус (работает или остановлена), время работы службы;
* **system**: информация о системе (загрузка системы, скорость работы жестких дисков);
* **time**: информация о времени (текущее время, время работы системы);
* **terminal\_services**: информация о удаленном рабочем столе (Terminal Services) - количество активных сессий, количество подключенных пользователей.

## Prometheus Exporter Blackbox

Prometheus Exporter Blackbox - это экспортер, который используется для проверки доступности и проверки ответов HTTP-сервисов и TCP-портов.

Среди возможностей, которые предоставляет prometheus-exporter-blackbox, можно выделить:

1. Проверка доступности: экспортер проверяет доступность TCP-портов и URL-адресов и сообщает о их статусе (доступен\не доступен).
2. Проверка ответа: экспортер может проверить, что HTTP-ответ на определенный URL-адрес содержит ожидаемый текст или совпадает с регулярным выражением

Конфигурация **Prometheus Exporter Blackbox** описывается в файле **%mon\_home%\prometheus-exporter-blackbox\blackbox.yml**.

```yaml
modules:
  http_2xx:
    http:
      no_follow_redirects: false
      preferred_ip_protocol: ip4
      valid_http_versions:
      - HTTP/1.1
      - HTTP/2
      valid_status_codes: []
    prober: http
    timeout: 5s
  http_post_2xx:
    prober: http
    http:
      method: POST
  tcp_connect:
    prober: tcp
  pop3s_banner:
    prober: tcp
    tcp:
      query_response:
      - expect: "^+OK"
      tls: true
      tls_config:
        insecure_skip_verify: false
  grpc:
    prober: grpc
    grpc:
      tls: true
      preferred_ip_protocol: "ip4"
  grpc_plain:
    prober: grpc
    grpc:
      tls: false
      service: "service1"
  ssh_banner:
    prober: tcp
    tcp:
      query_response:
      - expect: "^SSH-2.0-"
      - send: "SSH-2.0-blackbox-ssh-check"
  irc_banner:
    prober: tcp
    tcp:
      query_response:
      - send: "NICK prober"
      - send: "USER prober prober prober :prober"
      - expect: "PING :([^ ]+)"
        send: "PONG ${1}"
      - expect: "^:[^ ]+ 001"
  icmp:
    prober: icmp
  icmp_ttl5:
    prober: icmp
    timeout: 5s
    icmp:
      ttl: 5
```
