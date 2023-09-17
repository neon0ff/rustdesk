# Rustdesk
## Skript
### Перед установкой обновим всю софтину
<code>sudo apt update</code>

<code>sudo apt upgrade -y</code>
### Настроим фаервол
<code>sudo ufw allow 22</code>

<code>sudo ufw allow 21115:21119/tcp</code>

<code>sudo ufw allow 8000/tcp</code>

<code>sudo ufw allow 21116/udp</code>

<code>sudo ufw enable</code>
### Далее скачаем и запустим установщик
<code>sudo wget https://raw.githubusercontent.com/dinger1986/rustdeskinstall/master/install.sh</code>

<code>sudo chmod +x install.sh</code>

<code>sudo ./install.sh</code>
### Во время установки у нас спросят: IP или DNS/Domain — выбираем DNS/Domain вводя "2"
### Дальше скрипт нам предложить установить HTTP-сервер, который нужен для работы программы. Соглашаемся и вводим 1
### Когда всё будет готово, скрипт отдаст нам пароль администратора и публичны ключ — они нам понадобятся в будущем:
## Поднятие с помошью Docker
### Перед установкой обновим всю софтину
<code>sudo apt update</code>

<code>sudo apt upgrade -y</code>
### Настроим фаервол
<code>sudo ufw allow 22</code>
### Установим Docker-compose
<code>sudo apt install docker-compose -y</code>
### Скачаем репоззиторий с конф файлом
<code>sudo git clone https://github.com/rustdesk/rustdesk-server</code>
### Переходим в папку и редактирум docker-compose.yml
<code>cd rustdesk-server</code>

<code>sudo nano docker-compose.yml</code>
### Там меняем 2 строки
```
command: hbbs -r rustdesk.example.com:21117
command: hbbr
на
command: hbbs -r rust1desk1.yourdomain.com:21117 -k _
command: hbbr -k _
```
### Далее нужно открыть контейнеры и проверить ключи и убедиться что они одинаковые
### Откроем котейнер hbbs и найдет ключ и выпешем его
<code>sudo docker exec -it hbbs /bin/bash</code>

<code>cat id_ed25519.pub</code>
### Мы увидили наш ключ записали его
### Так же можно проверить и обычный приватный ключ
### Теперь выходим и открываем следующий контейнер
<code>exit</code>

<code>sudo docker exec -it hbbr /bin/bash</code>
### Так же открываем ключи и проверям что бы совпадали с прошлым
### К себе выписываем только публичный ключ


# LINKS
* [Habr](https://habr.com/ru/articles/672230/)
* [RustDesk](https://rustdesk.com/docs/en/self-host/install/)
* [RustDesk rus](https://rustdesk.com/docs/ru/)
