# Create-and-Host-a-Wordpress-Website-on-AWS-EC2

1- Create WordPress EC2 in AWS EC2 service (use basic settings Ununtu-t2Micro- Keypair - VPC{yourown or standart})- Launch Instance.

2- Do not forget to add Inbound Rule for PORT:22 SSH to connect Ec2.

3- If you want your IP adress to be static(not change every reboot) you should Allocate an ElasticIP from AWS and assign it to WordPress Ec2 (Warning: You will be charged by ElasticIP in AWS)

4- Click on your WordPress Ec2 and Connect using SSH (via Terminal or GitBash..)

5- ssh -i ~/Downloads/demo-key2.pem ubuntu@3.76.106.52 {demokey: will be your own keypair and IP adress will be your Public IP address}

6- We connect to EC2 now we install Apache webserver: && sudo apt install apache2

7- For crosscheck: http://{yourpublicIP} Apache page welcomes you.

8- We install PHP : && sudo apt update
                    && sudo apt install php
                    && php --version #For checking
                    && sudo apt install php-mysql php-curl php-xml php-mbstring php-imagick php-zip php-gd # WordPress module for PHP
9- We install MySQL: && sudo apt install mysql-server

10- sudo mysql -u root
ALTER USER 'root'@localhost INDETIFIED WITH mysql_native_password BY 'Testpassword@123' ;
