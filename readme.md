# Steps to create a Virtual Domainsin Ubuntu #
## Install apache and enable modules
1. sudo apt update
2. sudo apt install apache2
3. sudo a2enmod rewrite
4. systemctl restart apache2
5. sudo a2enmod vhost_alias

## Add a symbolic link
ln -s /home/silverliningco/myrepos/sunacool.coolcalc.com/www /var/www/html/sunacool.coolcalc.com

## Configure your virtual domain
cd /etc/apache2/sites-available/

sudo vim misite.pe.conf
```<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName misite.pe
    DocumentRoot /home/silverliningco/Documentos/anthara/intranet
    <Directory /home/silverliningco/Documentos/anthara/intranet>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
## Enable your virtual domain
sudo a2ensite misite.pe.conf
systemctl restart apache2

## Update your host file
sudo vim /etc/hosts
```
127.0.0.1       misite.pe
```
sudo systemctl restart apache2

# If permisions denied error
- Do a chmod +x on your user dir, and restart apache. 755 permissions should work. 
- sudo chmod +x /home/silverliningco/
