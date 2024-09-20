# [ENG](https://github.com/neon0ff/rustdesk/blob/main/README_ENG.md) | RUS
## Ручная настройка
##### Перед установкой обновим всю софтину
```bash
sudo apt update
```
```bash
sudo apt upgrade -y
```

##### Настроим файрволл
```bash
sudo ufw allow 22
```
```bash
sudo ufw allow 21115:21119/tcp
```
```bash
sudo ufw allow 8000/tcp
```
```bash
sudo ufw allow 21116/udp
```
```bash
sudo ufw enable
```

##### Далее скачаем и запустим установщик
```bash
sudo wget https://raw.githubusercontent.com/dinger1986/rustdeskinstall/master/install.sh
```
```bash
sudo chmod +x install.sh
```
```bash
sudo ./install.sh
```
##### Во время установки у нас спросят: IP или DNS/Domain — выбираем DNS/Domain вводя "2"
##### Дальше скрипт нам предложить установить HTTP-сервер, который нужен для работы программы. Соглашаемся и вводим 1
##### Когда всё будет готово, скрипт отдаст нам пароль администратора и публичны ключ — они нам понадобятся в будущем:

# Поднятие с помощью Docker
##### Перед установкой обновим весь софт
```bash
sudo apt update
```

```bash
sudo apt upgrade -y
```

##### Установим Docker и Docker-compose по инструкции на [этой ссылке](https://totaku.ru/ustanovka-docker-i-docker-compose-na-ubuntu-22-04/)

##### Создаем и переходим в папку RustDesk
```bash
sudo mkdir RustDesk
```

```bash
cd RustDesk
```
##### Скачаем конфигурационный файл
```bash
sudo git clone https://github.com/neon0ff/rustdesk/blob/main/docker-compose.yml
```

```bash
sudo nano docker-compose.yml
```
##### Там меняем одну строку, там вместо ```rust1desk1.yourdomain.com``` пишем свой домен
```
command: hbbs -r rust1desk1.yourdomain.com:21117 -k _
```
##### Далее нужно проверить ключи и записать их, можно несколькими способами. 
##### Первый простой способ посмотреть его после запуска контейнера в директории
```bash
cat RustDesk/data/id_ed25519.pub
```

> [!IMPORTANT]
> Главное записываем ключ вместе со знаком `=`

##### Второй способ - посмотреть логи докер контейнера где будет показан ключ
```bash
sudo docker logs hbbr</code>
```
##### Там мы увидим много информации, но нам нужна только одна информационная строка ``Key:`` и выглядит она примерно так:
```bash
[2024-06-14 07:27:24.981370 +00:00] INFO [src/rendezvous_server.rs:1191] Key: g1J0rV4WXwgnzvA2Ezqd0wns3PVMfovAbgHKHpt8QveE=
```

# LINKS
* [Habr](https://habr.com/ru/articles/672230/)
* [RustDesk](https://rustdesk.com/docs/en/self-host/install/)
* [RustDesk rus](https://rustdesk.com/docs/ru/)
