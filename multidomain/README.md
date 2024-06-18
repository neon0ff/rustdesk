# Поднятие мультидоменного RustDesk с помошью Docker
### Перед установкой обновим всю софтину
<code>sudo apt update</code>

<code>sudo apt upgrade -y</code>

### Установим Docker и Docker-compose по иснтрукции на [этой ссылке](https://totaku.ru/ustanovka-docker-i-docker-compose-na-ubuntu-22-04/)

### Создаеи и переходим в папку RustDesk
<code>sudo mkdir RustDesk</code>

<code>cd RustDesk</code>
### Скачаем конфигурационный файл
<code>sudo git clone https://github.com/neon0ff/rustdesk/blob/main/multidomain/docker-compose.yml</code>

<code>sudo nano docker-compose.yml</code>
### Там меняем 3 строки, там вместо ```rust1desk1.yourdomain.com``` и последующие пишем свои домены
```
command: hbbs -r rust1desk1.yourdomain.com:21117 -k _
```
### Далее нужно проверить ключи и записать их, можно несколькими способами
### Самый простой способ, посмотреть его после запуска контейнера в деректории
<code>cat RustDesk/data1/id_ed25519.pub</code>
<code>cat RustDesk/data2/id_ed25519.pub</code>
<code>cat RustDesk/data3/id_ed25519.pub</code>

<sub>Самое главное записываем ключ вместе со знаком "="</sub>

### Второй способ - посмотреть логи докер контейнера где будет показан ключ
<code>sudo docker logs hbbr1</code>
<code>sudo docker logs hbbr2</code>
<code>sudo docker logs hbbr2</code>

### Там мы увидим много информации но нам нужна только одна информационная строка ``Key:`` и выглядит она примерно так:
```bash
[2024-06-14 07:27:24.981370 +00:00] INFO [src/rendezvous_server.rs:1191] Key: g1J0rV4WXwgnzvA2Ezqd0wns3PVMfovAbgHKHpt8QveE=
```
