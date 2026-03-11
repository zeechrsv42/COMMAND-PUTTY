# COMMAND-PUTTY
FOLLOW PO BOSSS!

WEB
(1) apt update 
(2) apt install apache2 -y
(3) apt install php php-{cli,mysql,gd,xml,curl,mbstring,intl,zip,soap,bcmath} -y

>TERUSIN KE DB-SERVER DULU

(12) cd /var/www/html/
(13) wget https://download.moodle.org/download.php/direct/stable405/moodle-latest-405.tgz
(14) tar -zxvf moodle-latest-405.tgz
(15) mkdir /var/www/moodledata
(16) chown -R www-data:www-data /var/www/moodledata/
(17) chmod -R 777 /var/www/moodledata/
(18) chown -R www-data:www-data moodle
(19) chmod -R 777 moodle
(20) nano /etc/php/8.3/apache2/php.ini > CTRL W > (MAX_INPUT_VAR) diganti (5000)
(21) systemctl restart apache2




DB
(1) apt update
(2) apt install mariadb-server -y

(4) nano etc/mysql/mariadb.conf.d/50-server.cnf (di ganti bind-address= 0.0.0.0)
(5) systemctl restart mariadb
(6) mysql
(7) CREATE DATABASE moodle DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci
(8) CREATE USER 'zefanya'@'%' IDENTIFIED BY '12345678' ;
(9) GRANT ALL PRIVILEGES ON moodle.* TO 'zefanya'@'%';
(10) FLUSH PRIVILEGES ;
(11) EXIT



LANJUTAN WEB TO EXTERNAL
nano /var/www/html/moodle/config.php

$CFG->wwwroot = 'http://' .$_SERVER['HTTP_HOST'] . '/moodle' ;

ctrl X -> Y