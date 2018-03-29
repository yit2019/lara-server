### Install Packages:
```bash
apt-get install software-properties-common
apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
add-apt-repository 'deb [arch=amd64,i386,ppc64el] http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu xenial main'
add-apt-repository -y 'ppa:ondrej/php'
add-apt-repository -y 'ppa:ondrej/nginx'
add-apt-repository -y ppa:certbot/certbot
apt-get update
apt-get -y install gcc curl gzip sqlite3 git tar software-properties-common nginx php7.2-fpm php7.2-xml php7.2-bz2  php7.2-zip php7.2-mysql php7.2-intl php7.2-gd php7.2-curl php7.2-soap php7.2-mbstring python-certbot-nginx mariadb-server
#
```
### Clone git repo
```bash
git clone https://github.com/AfzalH/lara-server.git && cd lara-server
```

### Create a site: Enter domain
```bash
echo 'Enter Site Domain [site.com]:' && read site_com
```

...And Change config
```bash
cp nginx/srizon.com /etc/nginx/sites-available/$site_com
sed -i "s/srizon.com/${site_com}/g" /etc/nginx/sites-available/$site_com
mkdir /var/www/$site_com
mkdir /var/www/$site_com/public
touch /var/www/$site_com/public/index.php
ln -s /etc/nginx/sites-available/$site_com /etc/nginx/sites-enabled/$site_com
service nginx reload
```

### Edit to test out
```bash
nano /var/www/$site_com/public/index.php
```

### Clear document root
```bash
rm -rf /var/www/$site_com/public
```
### Move to document root to clone laravel project
```bash
cd /var/www/$site_com
```

Now clone your project. Create database and connect on .env

### https
```bash
certbot --nginx
```
