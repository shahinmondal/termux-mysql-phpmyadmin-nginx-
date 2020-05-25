
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


location /phpmyadmin {
           root /usr/share/;
           index index.php index.html index.htm;
           location ~ ^/phpmyadmin/(.+\.php)$ {
                   try_files $uri =404;
                   root /usr/share/;
                   fastcgi_pass unix:/run/php/php7.2-fpm.sock;
                   fastcgi_index index.php;
                   fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                   include /etc/nginx/fastcgi_params;
           }
           location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
                   root /usr/share/;
           }
    }
    
    


server {
        listen 80 default_server;
        listen [::]:80 default_server;
        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.php index.html index.htm index.nginx-debian.html;

        server_name 192.168.0.111;

        location ~ \.php$ {
           include snippets/fastcgi-php.conf;
           fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
           include fastcgi_params;
       }
}

sudo nginx -t

sudo rm -rf /etc/nginx/sites-enabled/default
 sudo ln -s /etc/nginx/sites-available/phpmyadmin.conf /etc/nginx/sites-enabled/
 
 














sudo apt install pv
pv ~/fulldump.sql | mysql


sudo apt install mysqltuner

mysqltuner

