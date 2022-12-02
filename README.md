# Create-and-Host-a-Wordpress-Website-on-AWS-EC2

1- Create WordPress EC2 in AWS EC2 service (use basic settings Ununtu-t2Micro- Keypair - VPC{yourown or standart})- Launch Instance.

2- Do not forget to add Inbound Rule for PORT:22 SSH to connect Ec2.

3- If you want your IP adress to be static(not change every reboot) you should Allocate an ElasticIP from AWS and assign it to WordPress Ec2 (Warning: You will be charged by ElasticIP in AWS)

4- Click on your WordPress Ec2 and Connect using SSH (via Terminal or GitBash..)

5- ssh -i ~/Downloads/demo-key2.pem ubuntu@3.76.106.52 {demokey: will be your own keypair and IP adress will be your Public IP address}

6- We will install LAMP Stack in Ubuntu: L: Linux A: Apache M: MySQL P: PHP

![image](https://user-images.githubusercontent.com/113843658/205323487-b6421a2f-cf7b-4298-95ba-fcb1edff43a9.png)


7- We update all packages : && sudo apt update && apt upgrade -y

8- Install Apache and basic packages: && sudo apt install apache2 wget nano -y

9- Install MySQL system called :MariaDB: && sudo apt install mariadb-server -y

10- Setting up MariaDB Server:  && sudo service mariadb start

                                && sudo mysql_secure_installation

                                Enter current password for root (enter for none): {hit enter}

                                Set root password? [Y/n] Y
                                
                                New password: ********* {create a new password for root}
                                
                                Re-enter new password: *********
                               
                                Password updated successfully!
                                
                                Reloading privilege tables...
                                
                                 ... Success!

                                And Hit 'Y' for all Y-N questions.

11- Create a database:  && sudo mariadb

                        MariaDB> create database db_wordpress; {create a database called db_wordpress}

                        MariaDB> exit

12- Install PHP :   && sudo apt install php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath -y

                    && sudo service apache2 restart#

                    You can test that PHP is working properly:  && cd /var/www/html

                                                                && sudo vim test.php {  <?php
                                                                                    
                                                                                        phpinfo();

                                                                                        ?>}

                                                                In your browser: http://{your public ip}/test.php {php test page must be seen}

                                                                remove the test file: && sudo rm test.php

13- We are at:  && cd /var/www/html

14- Download the latest version of WordPress :  && sudo wget http://wordpress.org/latest.tar.gz

                                                && sudo tar -zxvf latest.tar.gz  #Untar the file 

                                                Goto browser : http://{your public IP}/wordpress #installation screen appeears
                                        
15- Fill the information about your database.

![image](https://user-images.githubusercontent.com/113843658/205323307-0695d44c-30dc-45f9-9de7-73066fd26e39.png)


16- In the next screen copy php code and paste it : && cd /var/www/html/wordpress

                                                    && sudo vim wp-config.php {paste your code in this file and save it}

                                                    Run the installation.

17- Your last step for installation. Just fill your WordPress configuration.

![image](https://user-images.githubusercontent.com/113843658/205323355-4f1be2d9-40f4-4ffe-9a3f-7ade69abc7d4.png)
