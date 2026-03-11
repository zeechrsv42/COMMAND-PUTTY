# COMMAND-PUTTY

WEB
apt update 
apt install apache2 -y
apt install php php-{cli,mysql,gd,xml,curl,mbstring,intl,zip,soap,bcmath} -y
cd /var/www/html/
wget https://download.moodle.org/download.php/direct/stable405/moodle-latest-405.tgz
tar -zxvf moodle-latest-405.tgz
mkdir /var/www/moodledata
chown -R www-data:www-data /var/www/moodledata/
chmod -R 777 /var/www/moodledata/
chown -R www-data:www-data moodle
chmod -R 777 moodle
nano /etc/php/8.3/apache2/php.ini > CTRL W > (MAX_INPUT_VAR) diganti (5000)
systemctl restart apache2




DB
apt update
apt install mariadb-server -y
nano /etc/mysql/mariadb.conf.d/50-server.cnf (di ganti bind-address= 0.0.0.0)
systemctl restart mariadb
mysql
CREATE DATABASE moodle DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'zefanya'@'%' IDENTIFIED BY '12345678' ;
GRANT ALL PRIVILEGES ON moodle.* TO 'zefanya'@'%';
FLUSH PRIVILEGES ;
EXIT



LANJUTAN EXTERNAL
nano /var/www/html/moodle/config.php

$CFG->wwwroot = 'http://' .$_SERVER['HTTP_HOST'] . '/moodle' ;

ctrl X -> Y
