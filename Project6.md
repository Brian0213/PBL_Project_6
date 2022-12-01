## Documentation for Project 5: IMPLEMENT A CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS)

- TASK – Implement a Client Server Architecture using MySQL Database Management System (DBMS).
To demonstrate a basic client-server using MySQL Relational Database Management System (RDBMS), follow the below instructions

Create and configure two Ubuntu-based virtual servers (EC2 instances in AWS):

**Preparing prerequisites**

- Create two new EC2 Instance of t2.nano family with Ubuntu Server 20.04 LTS (HVM) image.

- On mysql server Ubuntu Server install MySQL Server software.
Interesting fact: MySQL is an open-source relational database management system. Its name is a combination of "My", the name of co-founder Michael Widenius’s daughter, and "SQL", the abbreviation for Structured Query Language:

- Update the package:

`sudo apt update`

![Sudo Apt Update Server](./image/sudo-apt-update.PNG)

- Upgrade the package:

`sudo apt upgrade`

![Sudo Apt Upgrade Server](./image/sudo-apt-upgrade.PNG)

- Install my sql server:

`sudo apt-get install mysql-server`

![MySql Server Install](./image/mysql-server-install-output.PNG)

- create user in mysql server:

`create user 'john'@'%' identified by 'password';`

`grant all privileges on *. * to 'john'@'%';  flush privileges;`

- On mysql client Ubuntu Server install MySQL Client software:

- Update the package:

`sudo apt update`

![Sudo Apt Update Client](./image/sudo-apt-update-client.PNG)

- Upgrade the package:

`sudo apt upgrade`

![Sudo Apt Upgrade Client](./image/sudo-apt-upgrade-client.PNG)

- Install my sql client:

`sudo apt-get install mysql-client`

![MySql Client Install](./image/mysql-clientr-install-output.PNG)

- By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ – allow access only to the specific local IP address of your ‘mysql client’.

![Inbound Rule](./image/inbound-rule-output.PNG)

- You might need to configure MySQL server to allow connections from remote hosts:

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`

![MySql Client Install](./image/configure-mysql-server.PNG)

- From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH. You must use the mysql utility to perform this action:

`mysql -u john -h 3.144.183.45 -p`

![MySql Client Install](./image/client-server-connection.PNG)

- Check that you have successfully connected to a remote MySQL server and can perform SQL queries:

`Show databases;`

![Success Connection](./image/confirm-connect.PNG)

