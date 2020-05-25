


pkg install wget openssl-tool proot -y && hash -r && wget https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/Installer/Ubuntu/ubuntu.sh && bash ubuntu.sh

./start-ubuntu.sh

apt update&&apt upgrade

apt install sudo

sudo apt install mysql-server


sudo service mysql restart

usermod -d /var/lib/mysql mysql

mysqldump --all-databases --routines -u root -p > ~/fulldump.sql

sudo apt update

sudo apt install phpmyadmin php-mbstring php-gettext

sudo phpenmod mbstring

sudo mysql

SELECT user,authentication_string,plugin,host FROM mysql.user;

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

FLUSH PRIVILEGES;

SELECT user,authentication_string,plugin,host FROM mysql.user;

mysql -u root -p

exit

sudo apt-get install nginx php7.2 php7.2-common php7.2-mysql php7.2-mbstring php7.2-fpm php7.2-cgi php7.2-common php-pear php-gettext 

sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin

sudo nano /etc/nginx/sites-available/phpmyadmin.conf

sudo nginx -t

sudo rm -rf /etc/nginx/sites-enabled/default

sudo ln -s /etc/nginx/sites-available/phpmyadmin.conf /etc/nginx/sites-enabled/
 
sudo apt install pv

pv ~/fulldump.sql | mysql

sudo apt install mysqltuner

mysqltuner
