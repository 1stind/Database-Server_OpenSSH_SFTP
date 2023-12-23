# Create Database Server SFTP and Mail Server
## 22.83.0859 Indra Bagas Pratama
#
## Deskripsi
- Database server with Mysql PhpMyadmin
- Secure Shell & Secure File Transfer Protocol With OpenSSH
- DHCP Server
- Mail Server

## Requirements
- Ubuntu Server 22.04
- Storange minimal 40 GB
- RAM 4 GB ++

## Installation
### Configure Apache
Step 1: Update Repo

```sh
apt update && upgrade -y
```
Step 2: Install Apache

```sh
apt-get install apache2 -y
```
```sh
systemctl status apache2
```
### Configure Database Server 
Step 1: Install Mysql Server
```sh
apt install mysql-server -y
```
Step 2: Konfigurasi Mysql Server
```sh
mysql_secure_installation
```

* current password root awal belum ditentukan, maka dari itu pilih n

* untuk membuat password root y dan masukkan password

* remove anonymous users? y

* disallow root login remotely? y

* remove test database and access to it? y

* reload privilege tables now? y

Step 3: Testing

```sh
mysql -u root -p
```
```sh
create database test;
```
```sh
show database;
```
```sh
exit;
```
Step 4: Install Php
```sh
apt-get install php php-mysql libapache2-mod-php php-cli php-cgi php-gd mysql-server mysql-client zip -y
```
Step 5: Install PhpMyadmin

```sh
apt install phpmyadmin -y
```
* configure phpmyadmin pada pilihan apache2 dan lighttpd, sesuaikan pada service web server yang digunakan
* configure database with dbconfig-common. y

Step 5: hak akses direktori phpmyadmin

```sh
 ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
```
```sh
a2enconf phpmyadmin.conf
```
```sh
systemctl restart apache2
```
Step 6: Testing

```sh
http:192.168.0.0/phpmyadmin
```
* ganti ip 192.168.0.0 sesuai ip pada ubuntu yang digunakan

### Secure Shell & Secure File Transfer Protocol With OpenSSH
Step 1: Install openssh-server
```sh
apt install openssh-server
```
Step 2: Konfigurasi openssh-server
```sh
nano /etc/ssh/sshd.conf
```
* 
*
*

Step 3: Testing remote SSH
```sh
ssh root@192.168.0.0
```
Step 4: Testing SFTP
```sh
sftp://192.168.0.0:22
```
* 
*

### Configure DHCP Server
### Configure Mail Server- 

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
