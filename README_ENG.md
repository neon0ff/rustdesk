ENG | [RUS](https://github.com/neon0ff/rustdesk/blob/main/README.md)
## Manual Setup

##### Before installation, update all software:

```bash
sudo apt update
```

```bash
sudo apt upgrade -y
```

##### Configure the firewall:

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

##### Next, download and run the installer:

```bash
sudo wget https://raw.githubusercontent.com/dinger1986/rustdeskinstall/master/install.sh
```

```bash
sudo chmod +x install.sh
```

```bash
sudo ./install.sh
```

##### During the installation, you'll be asked to choose between IP or DNS/Domain. Select "DNS/Domain" by entering "2".
##### The script will also prompt you to install an HTTP server needed for the program to work. Agree by entering "1".
##### When the setup is complete, the script will provide you with the admin password and a public key — these will be needed later.

---

## Setup Using Docker

##### Before installation, update all software:

```bash
sudo apt update
```

```bash
sudo apt upgrade -y
```

##### Install Docker and Docker Compose in one command
```bash
curl -fsSL https://test.docker.com | sudo sh
```

##### Create and navigate to the RustDesk folder:

```bash
sudo mkdir RustDesk
```

```bash
cd RustDesk
```

##### Download the configuration file:

```bash
sudo git clone https://github.com/neon0ff/rustdesk/blob/main/docker-compose.yml
```

```bash
sudo nano docker-compose.yml
```

##### Replace the following line with your domain:

```
command: hbbs -r rust1desk1.yourdomain.com:21117 -k _
```

##### Next, you need to verify and record the keys. There are a few ways to do this.

##### The first, simplest way is to view it after starting the container in the directory:

```bash
cat RustDesk/data/id_ed25519.pub
```

> [!IMPORTANT]
> Make sure to record the key including the `=` sign.

##### The second way is to check the Docker container logs where the key will be displayed:

```bash
sudo docker logs hbbr
```

##### You'll see a lot of information, but you need to find the line that starts with `Key:`. It should look something like this:

```bash
[2024-06-14 07:27:24.981370 +00:00] INFO [src/rendezvous_server.rs:1191] Key: g1J0rV4WXwgnzvA2Ezqd0wns3PVMfovAbgHKHpt8QveE=
```

---

## LINKS
* [Habr](https://habr.com/ru/articles/672230/)
* [RustDesk](https://rustdesk.com/docs/en/self-host/install/)
* [RustDesk (Russian)](https://rustdesk.com/docs/ru/)
