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
