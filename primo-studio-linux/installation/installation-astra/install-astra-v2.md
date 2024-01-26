# Установка Primo RPA Studio Linux на Astra Linux

## Установка дополнительных компонентов

Выберите активную версию Python 3.7:  

`sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7`  

Об успехе будет свидетельствовать ответ:  

`update-alternatives: using /usr/bin/python3.7python to provide /usr/bin/python (python) in auto mode`  

Проверьте, что версия выбрана верно:  

`python -V`  

Распакуйте архив StudioLinuxAdds.deb.zip в удобный каталог, например: `/home/user`.  

Скачать архив можно [здесь](https://disk.primo-rpa.ru/index.php/s/cmapanywLsMkZzs).  

Перейдите в каталог python3-pyatspi и установите все пакеты:  

`cd /home/user/python3-pyatspi`
`sudo dpkg -i *.deb`  

Перейдите в каталог imagemagick и установите все пакеты:  

`cd /home/user/imagemagick`
`sudo dpkg -i *.deb`

Проверьте корректность установки:  

`convert -version`

Перейдите в каталог xdotool и установите все пакеты:

`cd /home/user/xdotool`
`sudo dpkg -i *.deb`

Проверьте корректность установки:

`xdotool –version`

Установите xsel:

`sudo apt-get update`
`sudo apt-get -y install xsel`

## Установка Cтудии

Распакуйте архив Primo.Studio.Linux.zip в удобный каталог, например: `/home/user`. 

Создайте каталог:

`sudo mkdir /opt/Primo/`

Содержимое папки linux-x64 перенесите в `/opt/Primo/Studio`

`sudo mv /home/user/linux-x64/ /opt/Primo/Studio/`

Задайте права:

`sudo chmod -R 777 /opt/Primo/Studio/`

## Установка расширения для браузера Хром

Откройте браузер Хром, выберите пункт меню **Настройки и управление Google Chrome > Расширения > Управление расширениями**, далее на странице **Расширения** установите настройку **Режим разработчика**:



