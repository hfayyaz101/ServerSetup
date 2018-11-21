# ServerSetup

## Reference

1. https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04
2. https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04
3. https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04
4. https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-ubuntu-18-04
5. https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-18-04
6. https://www.linuxbabe.com/mail-server/ubuntu-16-04-iredmail-server-installation
7. https://docs.iredmail.org/install.iredmail.on.debian.ubuntu.html
8. https://iredmail.org/download.html
9. https://www.justcolin.co.uk/iredmail-ssl-certificate-installation-with-lets-encrypt/

WP only: NGINX
to resolve permalinks issue.
go to /etc/nginx/sites-availabel
nano into domain name
and add
try_files $uri $uri/ /index.php?$args;
and # other one in location.



veryone experiencing this issue should execute these commands:
```
sudo usermod -aG www-data $USER
```
Adds the currently logged in user to the www-data group.
```
sudo chown -R www-data:www-data /var/www
```
Changes the ownership of the /var/www directory to www-data group.
```
sudo chmod -R 774 /var/www
```
Sets the proper permissions so you can upload files via sftp, manage files via command-line, and upload plugins and media directly in WordPress.

The following is not aimed toward the original poster, but toward a couple of the comment authors:

If this doesn't fix the issue you're having, you've got something else wrong and bashing DO is not going to help anyone. If you want a managed server, look for hosting elsewhere. If you need help, ask someone or hire an admin that knows how to not only 'set things up' but knows how to secure your server as well. You'll be glad you did. DO is not for novices, even if they have a lot of tutorials.

## Max File Size

Modify NGINX Configuration File
```
sudo nano /etc/nginx/nginx.conf
```
Search for this variable: client_max_body_size. If you find it, just increase its size to 100M, for example. If it doesn’t exist, then you can add it inside and at the end of http
```
client_max_body_size 100M;
```
Restart nginx to apply the changes.
```
sudo service nginx restart
```
Modify PHP.ini File for Upload Limits

It’s not needed on all configurations, but you may also have to modify the PHP upload settings as well to ensure that nothing is going out of limit by php configurations.

If you are using PHP5-FPM use following command,
```
sudo nano /etc/php5/fpm/php.ini
```
If you are using PHP7.0-FPM use following command,
```
sudo nano /etc/php/7.0/fpm/php.ini
```
Now find following directives one by one
```
upload_max_filesize
post_max_size
```
and increase its limit to 100M, by default they are 8M and 2M.
```
upload_max_filesize = 100M
post_max_size = 100M
```
Finally save it and restart PHP.

PHP5-FPM users use this,
```
sudo service php5-fpm restart
```
PHP7.0-FPM users use this,
```
sudo service php7.0-fpm restart
```
It will work fine !!!
