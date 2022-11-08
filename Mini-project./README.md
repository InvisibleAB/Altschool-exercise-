## Configuration guide 
### Setup Virtual machine running on Debioan 11
### Install following packages
-  Git
-  Apache 
-  Wget 
-  Curl 
-  Php 8.1 and it's dependencies
-  Mysql/MariaDb Database
-  Composer

#### 1. Update Operating System
```
sudo apt install apache2
```
#### 2. Install (Git, wget, curl)
```
sudo apt install -y wget git  curl
```

#### 3. Install Apache
```
sudo apt install -y apache2
```

#### 4. Start Apache 
```
sudo systemctl start apache2
```
#### 5. Enable Apache to start on boot time
```
sudo systemctl enable apache2
```

#### 6. Install Php 8.1 and it's dependencies
First, install the required packages
```
sudo apt-get install ca-certificates apt-transport-https software-properties-common -y
```

Once all the packages are installed, add a Sury repository to APT 
```
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/sury-php.list
```

Next, download and add the GPG key
```
wget -qO - https://packages.sury.org/php/apt.gpg | apt-key add -
```
Once you are done, update the repository
```
sudo apt-get update -y
```
Now, you can install the PHP 8.1 
```
sudo apt-get install php8.1 libapache2-mod-php php8.1-dev php8.1-zip php8.1-curl php8.1-mbstring php8.1-mysql php8.1-gd php8.1-xml
```
Verify if PHP is installed
```
php -v
```

#### 7. Install Mysql 
```
sudo apt install mysql-server
```
#### 8. Start Mysl
```
sudo systemctl start mysql
```
#### 9. Enable Mysql to start on boot time
```
sudo systemctl enable mysql
```
#### 10. Create databse
Login to mysql 
```
sudo  mysql -u root 
```
Create database and user which will later be used 
```
CREATE DATABASE <database>;
```
```
CREATE USER '<user>'@'localhost' IDENTIFIED BY '<password>';
```
```
GRANT ALL PRIVILEGES ON <databse>.* TO '<user>'@'localhost';
```
```
FLUSH PRIVILEGES;
```
```
EXIT
```

#### 11. Install Composer
Download composer
```
curl -sS https://getcomposer.org/installer | php
```
Move composer file path to /usr/local/bin path
```
sudo mv composer.phar /usr/local/bin/composer
```
Make it executable 
```
sudo chmod +x /usr/local/bin/composer
```
#### 12. Clone the repo
Navigate to the webroot directory
```
sudo cd /var/www/html
```
Clone the repo
```
sudo git clone https://github.com/f1amy/laravel-realworld-example-app.git
```
navigate to the directory
```
cd laravel-realworld-example-app
```
#### 13. Change  the laravel document root permissions 
```
sudo chown -R www-data:www-data /var/www/html/laravel-realworld-example-app
```
```
sudo chmod -R 755 /var/www/html/laravel-realworld-example-app
```
#### 14. Edit the .env file
```
sudo vi .env
```
Change the following : DB_DATABASE, DB_PASSWORD and DB_USERNAME to the to the values assinged when ou created  mysql database
```php
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE= "Input your database name here"
DB_USERNAME= " "Input your database username here"
DB_PASSWORD=e"Input your mysql user password here"
```

#### 15. Composer
```
composer create-project
```
```
php artisan migrate:fresh
```

#### 16. Configure Apache to Host Laravel
Create Apache Virtual host configuration file for laravel
```
sudo vi /etc/apache2/sites-available/laravel.conf
```
Add the following to the file
```php
<VirtualHost *:80>
    ServerAdmin admin@altschool.me
    ServerName laravel.example.com
    DocumentRoot /var/www/html/laravel-realworld-example-app/public
    
    <Directory /var/www/html/laravel-realworld-example-app/public>
        Options Indexes MultiViews
        AllowOverride None
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
Save and close

#### 17. Activate the virtual host created 
```
sudo a2enmod rewrite
```
```
sudo a2ensite laravel.conf
```
Reload apache 
```
sudo systemctl restart apache2
```

#### 18. Edit the local dns file
```
sudo vi /etc/hosts
```
Add the ip address and ServerName assigned in laravel virtual host file





