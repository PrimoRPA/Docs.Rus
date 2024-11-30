# Установка Docker

## Файлы из комплекта поставки

Скопируйте на каждую целевую машину из группы файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                       | Описание           | 
| -------------------------- | ------------------ | 
| `docker/docker-27.3.1.tgz` | Дистрибутив Docker | 


## Установка Docker

Настоящее краткое руководство основано на официальной инструкции - [Install Docker Engine from binaries](https://docs.docker.com/engine/install/binaries/).

### 1. Загрузка архива

При наличии интернета, загрузите свежий архив с официального сайта. 

В отсутствие интернета воспользуйтесь предоставленной версией 27.3.1.

### 2. Распаковка архива
Распакуйте архив во временную папку: 

{% code title="" overflow="wrap" lineNumbers="true" %}

```
mkdir -p install/docker
cd install/docker
tar xzvf /srv/samba/shared/install/docker/install/docker/docker-27.3.1.tgz
```

{% endcode %}


### 3. Расположение компонентов

Переместите распакованные компоненты Docker в /usr/bin/:
```
sudo cp docker/* /usr/bin/
```

### 4. Установка зависимостей
Установите зависимости:
```
mkdir -p install/iptables
```
```
yes | sudo unzip /srv/samba/shared/install/docker/install/iptables.zip -d install/iptables
```
```
sudo dpkg -i install/iptables/*.deb
```

### 5. Установка docker-compose

Воспользуйтесь командой:
```
sudo dpkg -i /srv/samba/shared/install/docker/install/docker/docker-compose-plugin_2.27.1-1~debian.10~buster_amd64.deb
```

### 6. Установка системных служб

```
sudo cp /srv/samba/shared/install/docker/docker.service /etc/systemd/system/
```

```
sudo systemctl enable docker.service
```

```
sudo systemctl daemon-reload
```

```
sudo systemctl restart docker
```

## Раздача прав 

Добавьте пользователей, которые будут пользоваться командой docker и docker-compose в группу docker:
```
sudo usermod -aG docker agent
```
Если текущий пользователь в их числе, зарегистрируйте его в группе docker:
```
newgrp docker
```

## Что дальше
Выполните установку компонентов группы целевых машин NLP.
* [Агент Logics-сервера](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/target-machines-nlp/installation-agent)
* [Logics-сервер](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/target-machines-nlp/installation-logics-server)
* [Агент LLM-ядра](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/target-machines-nlp/installation-llm-core-agent)
* [LLM-ядро](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/target-machines-nlp/installation-llm-core)
