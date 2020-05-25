
pkg install wget openssl-tool proot -y && hash -r && wget https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/Installer/Ubuntu/ubuntu.sh && bash ubuntu.sh

./start-ubuntu.sh

apt update&&apt upgrade

apt install sudo

sudo apt install mysql-server


sudo service mysql restart

usermod -d /var/lib/mysql mysql

mysqldump --all-databases --routines -u root -p > ~/fulldump.sql

sudo apt install pv
pv ~/fulldump.sql | mysql


sudo apt install mysqltuner

mysqltuner

