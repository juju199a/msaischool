1. Create Resource Group
	- 리소스 그룹: 5b043-cloud-group5
	- 영역 : (Asia Pacific) Korea Central

2. Create Virtual Machine
	- 가상 머신 이름: 5b043-wordpress-vm5
	- 이미지: Ubuntu Server 24.04 LTS - x64 Gen2
	- 인증 형식: SSH 공개 키
	- 인바운드 포트 선택: HTTP (80), HTTPS (443), SSH (22)
	- VM 삭제 시 공용 IP 및 NIC 삭제: tick
	- 프라이빗 키 및 다운로드

3. Connect Virtual Machine
	- ssh -i ~\Downloads\~key.pem azureuser@1.1.1.1

4. Ubuntu Update
	- sudo apt update -y
	- sudo apt upgrade -y

5. Install package
	- sudo apt install apache2 mariadb-server php php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap libapache2-mod-php php-mysql -y

6. Start Web Server & enable Automatic Start
	- sudo systemctl start apache2
	- sudo systemctl enable apache2

7. Install MariaDB & Create DB
	- sudo mysql_secure_installation
		(enter n n y y y y)
	- sudo mysql -u root
	- create database wordpress;
	- show databases;
	- create user 'wordpress'@'localhost' IDENTIFIED BY '';
	- grant all privileges on wordpress.* to 'wordpress'@'localhost';
	- flush privileges;
	- show grants for 'wordpress'@'localhost';
	- exit
	
8. Install WordPress
	- cd /var/www/
	- sudo wget http://wordpress.org/latest.tar.gz
	- sudo tar -xvzf latest.tar.gz
	- sudo rm -rf html
	- sudo rm latest.tar.gz
	- sudo mv wordpress html

9. Change permission
	- sudo chown -R www-data:www-data /var/www/html
	- sudo chmod -R 775 /var/www/html

10. Connect WordPress
	- http://1.1.1.1
	- English or Korean
	- Database Name: wordpress
	- Username: wordpress
	- Password:
	- Database Host: localhost
	- Table Prefix: wp_

11. Set the information
	- Site Title : My First WordPress
	- Username: 5b043
	- Password: 1111
	- Confirm use of weak Password
	- Your Email: abc@gmail.com
	- Log in

12. Install SSL Certificate
	- DNS 이름: 구성되지 않음 (Click)
	- DNS 이름 레이블: first-5b043-wordpress5
	- sudo apt install python3-certbot-apache -y
	- sudo certbot --apache -d 'first-5b043-wordpress5.koreacentral.cloudapp.azure.com'

13. Modify broken page 
	- wp-admin > Settings > General
	- WordPress Address (URL): https://first-5b043-wordpress5.koreacentral.cloudapp.azure.com/
	- Site Address (URL): https://first-5b043-wordpress5.koreacentral.cloudapp.azure.com/
	- Save Changes > Advanced > Procceed
	- *(Reference) 
	- sudo vi wp-config.php
	- define('WP_HOME', 'http://~')
	- define('WP_SITEURL','http://~')

