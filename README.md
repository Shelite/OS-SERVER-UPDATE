# OS SERVER & SYSTEM ADMIN UPDATE
## _22.83.0830 fiqri andrian julianto_

## Install dan configurasi ssh

update dan install

```sh
sudo apt-get update
```

```sh
sudo apt install openssh-server
```

configurasi
```sh
sudo ufw allow ssh
```
```
sudo nano /etc/ssh/sshd_config
```
untuk bagian port ubah sesuai yg di ingin kan misal 2222
```
port 2222
```

install php
```sh
sudo apt install php libapache2-mod-php php-mysql
```

Download file ngrok

| VERSION LINUX |  LINK |
| ------ | ------ |
| ARM64 | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm64.tgz |
| ARM | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm.tgz |
| 32 bit | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-386.tgz |
