# Skript
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

# Поднятие с помошью Docker
### Перед установкой обновим всю софтину
<code>sudo apt update</code>

<code>sudo apt upgrade -y</code>

### Установим Docker и Docker-compose по иснтрукции на [этой ссылке](https://totaku.ru/ustanovka-docker-i-docker-compose-na-ubuntu-22-04/)

### Создаеи и переходим в папку RustDesk
<code>sudo mkdir RustDesk</code>

<code>cd RustDesk</code>
### Скачаем конфигурационный файл
<code>sudo git clone https://github.com/neon0ff/rustdesk/blob/main/docker-compose.yml</code>

<code>sudo nano docker-compose.yml</code>
### Там меняем одну строку, там вместо ```rust1desk1.yourdomain.com``` пишем свой домен
```
command: hbbs -r rust1desk1.yourdomain.com:21117 -k _
```
### Далее нужно проверить ключи и записать их, можно несколькими способами
### Самый простой способ посмотреть его после запуска контейнера в деректории
<code>cat RustDesk/data/id_ed25519.pub</code>

<sub>Самое главное записываем ключ вместе со знаком "="</sub>

### Второй способ - посмотреть логи докер контейнера где будет показан ключ
<code>sudo docker logs hbbr</code>

### Там мы увидим много информации но нам нужна только одна информационная строка ``Key:`` и выглядит она примерно так:
```bash
[2024-06-14 07:27:24.981370 +00:00] INFO [src/rendezvous_server.rs:1191] Key: g1J0rV4WXwgnzvA2Ezqd0wns3PVMfovAbgHKHpt8QveE=
```

# LINKS
* [Habr](https://habr.com/ru/articles/672230/)
* [RustDesk](https://rustdesk.com/docs/en/self-host/install/)
* [RustDesk rus](https://rustdesk.com/docs/ru/)
