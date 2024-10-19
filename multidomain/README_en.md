ENG | [RUS](https://github.com/neon0ff/rustdesk/blob/main/multidomain/README.md)
# Deploying a multi-domain RustDesk server using Docker
##### Before installing, we will update all the software.

```bash
sudo apt update
sudo apt upgrade -y

```

##### Install Docker and Docker Compose in one command
```bash
curl -fsSL https://test.docker.com | sudo sh
```

##### Next, create and go to the RustDesk directory.

```bash
mkdir RustDesk
cd RustDesk

```

##### Download the configuration file.

```bash
git clone https://github.com/neon0ff/rustdesk.git
cd rustdesk/multidomain
nano docker-compose.yml

```

##### In the file, change the `rust1desk1.yourdomain.com` and the following lines to your domain names.

```sh
command: hbbs -r rust1desk1.yourdomain.com:21117 -k
```
##### The easiest way to view the keys is by running the following commands in the directory:

```bash

cat RustDesk/data1/id_ed25519.pub

cat RustDesk/data2/id_ed25519.pub

cat RustDesk/data3/id_ed25519.pub

```

##### The most important thing to note is to write down the key along with the "=" symbol.

##### Alternatively, you can view the logs from the Docker container where the keys will be displayed. Run the following commands:

```bash
sudo docker logs hbbr1

sudo docker logs hbbr2

sudo docker logs hbbr3

```

##### In the logs, look for the line that starts with `Key:`, which will contain the key value. It will look something like this:

```bash
[2024-06-14 07:27:24.981370 +00:00] INFO [src/rendezvous_server.rs:1191] Key: g1J0rV4WXwgnzvA2Ezqd0wns3PVMfovAbgHKHpt8QveE=
