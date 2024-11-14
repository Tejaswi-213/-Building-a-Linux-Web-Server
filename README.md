# -Building-a-Linux-Web-Server
Everything is in  my read me 
Install Ubuntu:
Download the latest Ubuntu Server ISO and install it on your machine.
Follow the installation prompts to set up the server.
Secure the Server:
SSH Configuration:
sudo apt update
sudo apt install openssh-server
sudo ufw allow OpenSSH
sudo ufw enable

Firewall Configuration:
sudo ufw allow 'Apache Full'
sudo ufw status

Install Apache:
Apache Installation:
sudo apt update
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl enable apache2

Install MySQL:
MySQL Installation:
sudo apt install mysql-server
sudo mysql_secure_installation

Install PHP:
PHP Installation:
sudo apt install php libapache2-mod-php php-mysql

Deploying a Website:
Create Website Directory:
sudo mkdir -p /var/www/your_domain
sudo chown -R $USER:$USER /var/www/your_domain

Configure Virtual Host:
sudo nano /etc/apache2/sites-available/your_domain.conf

Add the following configuration:
<VirtualHost *:80>
    ServerAdmin admin@your_domain
    ServerName your_domain
    ServerAlias www.your_domain
    DocumentRoot /var/www/your_domain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

Enable Virtual Host:
sudo a2ensite your_domain.conf
sudo systemctl reload apache2

Testing and Monitoring:
Access your website by navigating to http://your_domain in a web browser.
Use monitoring tools to ensure the server is running smoothly:
htop
top
netstat -tuln
