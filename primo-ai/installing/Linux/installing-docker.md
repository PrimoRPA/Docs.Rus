# Установка Docker

## Файлы из комплекта поставки

Скопируйте на машину с AI Server файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                                                      | Описание                                                          | 
| ------------------------------------------------------------------------- | ----------------------------------------------------------------- | 
| `docker/docker/docker-27.3.1.tgz`                                         | Дистрибутив Docker                                                | 
| `docker/docker/docker.service`                                            | Файл службы для автоматического запуска Docker при старте системы | 
| `docker/docker/docker-compose-plugin_2.27.1-1~debian.10~buster_amd64.deb` | Плагин Docker-Compose                                             | 
| `docker/iptables.zip`                                                     | Пакет iptables                                                    | 


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
tar xzvf /srv/samba/shared/install/docker/docker/docker-27.3.1.tgz
```

{% endcode %}


### 3. Расположение компонентов

Переместите распакованные компоненты Docker в /usr/bin/:
```
sudo cp docker/* /usr/bin/
```

### 4. Установка зависимостей

Проверьте версию iptables командой:
```
apt policy iptables
```
Если пакет установлен и имеет версию > 1.4, пропустите этот шаг.

{% hint style="warning" %}
**Примечание**. Проверьте зависимости устанавливаемого пакета iptables версии 1.8.5-3~bpo10+1+b1_amd64. Выполняйте этот шаг только на чистой и поддерживаемой версии ОС. 
{% endhint %}

Установите зависимости:
```
mkdir -p install/iptables
```
```
yes | sudo unzip /srv/samba/shared/install/docker/iptables.zip -d install/iptables
```
```
sudo dpkg -i install/iptables/*.deb
```

### 5. Установка docker-compose

Воспользуйтесь командой:
```
sudo dpkg -i /srv/samba/shared/install/docker/docker/docker-compose-plugin_2.27.1-1~debian.10~buster_amd64.deb
```

### 6. Установка системных служб

```
sudo cp /srv/samba/shared/install/docker/docker/docker.service /etc/systemd/system/
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

## Создание группы docker 

Добавьте группу docker для использования команды docker:
```
sudo groupadd docker
```

## Раздача прав 

Добавьте пользователей, которые будут пользоваться командой docker и docker-compose в группу docker. Например, для пользователя docker_user:
```
sudo usermod -aG docker docker_user
```
Если текущий пользователь в их числе, зарегистрируйте его в группе docker:
```
newgrp docker
```
Выполните перезагрузку сервера, чтобы все пользователи получили требуемые полномочия на запуск команды docker.


