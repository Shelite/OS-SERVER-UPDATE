# OS SERVER & SYSTEM ADMIN 
22.83.0830_fiqri andrian julianto

menginstall web server di ubuntu 22.04 
menggunakan :
- apache 2
- phpmyadmin
- ssh
- ngrok
- winscp


#### Install dan configurasi ssh

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

restart service ssh
```
sudo systemctl restart ssh
```

kemudian jalankan di cmd
``` 
ssh server@'iplocalhost' -port 2222
```
#### install apache 2
```sh
sudo apt install apache2
```
jalankan apache 2
```
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
```
#### menginstall phpMyadmin

```
sudo apt install phpmyadmin
```
saat installasi :

- saat menginstall phpmyadmin jika muncul tampilan configurasi phpmyadmin centang pada bagian apache2 dengan menekan space bar, kemudian klik tab dan ok.
- jika muncul tampilan dbconfig pilih yes
- kemudian masukan password phpmyadmin nya

enable exkstensi php
```
sudo phpenmod mbstring
```

restart service
```
sudo systemctl restart apache2
```

untuk mengecek apache2 jalan apa tidak bisa memasukan https://iplocalhost dalam browser kesayangan dan untuk melihat phpmyadmin bia menuliskan  https://iplocalhost/phpmyadmin



## membuat agar website bisa public dengan ngrok

#### download win scp

- https://winscp.net/eng/download.php
install di windows, saya menggunakan winscp untuk memindahkan file html dan ngrok ke dalam ubuntu

#### Download file ngrok
- https://dashboard.ngrok.com/

login ke website ngrok dan download, untuk ubuntu saya menggunakan x86-64

| VERSION LINUX |  LINK |
| ------ | ------ |
| ARM64 | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm64.tgz |
| ARM | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm.tgz |
| x86-64 | https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz |
#### memindahkan file ngrok

buka aplikasi winscp dan masukan ip, port, username, dan password
untuk username bisa menggunakan root dan password
![image](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/80719b2f-a53f-4d63-a959-20ed377d5a1a)

langkah-langkah :
- extract file ngrok di windows kemudian pindah kan ke direktory ubuntu /home/'namauser', sebagai contoh nama user saya server

pindahkan ngrok ke /usr/local/bin
```
cd /home/server/
```
```
sudo mv ngrok /usr/local/bin 
```
buat permission pada file ngrok agar bisa di execute
```
chmod +x /usr/local/bin/ngrok
```
tambahkan auth-token ngrok yang ada di website ngrok dengan mengcopy authtoken nya dan paste di terminal ubuntu
![image](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/36826e5c-0969-4c16-a7e7-f23dfed1f631)

jalankan ngrok
```
ngrok http 80
```

dan copy url di ngrok nya sebagai contoh
![image](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/67362a14-7499-4cf4-90ad-305ad2d6553a)

kemudian paste ke web browser
![image](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/b26b8e14-8a44-4bf2-ba4e-16b2cf26ba43)

pindahkan html ke ubuntu menggunakan win scp di directory /home/'namauser'
![image](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/eabb6d84-023b-4a9d-bb35-e562464e4fb2)

pindah ke direktori /home/'namauser'
```
cd /home/server
```

pindah kan file html ke folder /var/www/html/
```
mv 'web project' /var/www/html/
cd /var/www/html/
```

kemudian buat direktori baru untuk membackup index.html
```
mkdir backup
mv index.html backup
```

kemudian keluarkan file html yang sudah di buat
```
cd 'web project'
mv *.html /var/www/html/
```

jalankan ngrok kembali
```
ngrok http 80
```

![Screenshot_20231211-195542](https://github.com/Shelite/OS-SERVER-UPDATE/assets/145192908/a50f5efd-bf46-4706-bb29-10f50ec70a27)

