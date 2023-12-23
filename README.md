# Create Database Server SFTP and Mail Server
## 22.83.0859 Indra Bagas Pratama
#
#
## Deskripsi
- Database server with Mysql PhpMyadmin
- Secure File Transfer Protocol With OpenSSH
- Secure Shell With OpenSSH
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
ganti ip 192.168.0.0 sesuai ip pada ubuntu yang digunakan
```sh
http:192.168.0.0/phpmyadmin
```
Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

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
