# Установка UI 

1. Подключитесь к серверу с Primo RPA AI Server от имени суперпользователя root. 
2. Распакуйте архив с UI в каталог `/app/Primo.AI/UI`:
   ```
   sudo unzip /srv/samba/shared/install/distr/UI.zip -d /app/Primo.AI/UI 
   ```
Этот каталог будет использоваться сервером nginx - укажите его в конфиге (/etc/nginx/nginx.conf > http > server > root).

## Что дальше

На этом развертывание компонентов на машине сервера можно считать оконченным. 

Теперь вы можете:
* [Установить и настроить ПО для целевой машины Умного OCR](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machine-smart-ocr).

ИЛИ:

* [Установить и настроить ПО для целевой машины NLP](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp).
