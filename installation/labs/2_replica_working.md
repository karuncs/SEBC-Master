##### install Mysql database 5.7 version

wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm

rpm -ivh mysql-community-release-el7-5.noarch.rpm

yum update

yum install mysql-server

systemctl start mysqld

##### on all nodes

yum install -y mysql


#####  to stop MySQl server if it running mysql
systemctl stop mysqld

##### Ensuer that Mysql start as a root
systemctl enable mysqld

##### download and copy JDBC driver on all nodes

Install the JDBC driver on the Cloudera Manager Server host, as well as any other hosts running services that require database access.

wget https://dev.mysql.com/downloads/file/?id=476197

tar zxvf mysql-connector-java-5.1.46.tar.gz

cp mysql-connector-java-5.1.46/mysql-connector-java-5.1.46-bin.jar /usr/share/java/mysql-connector-java.jar

mkdir -p /usr/share/java/

cp mysql-connector-java-5.1.31/mysql-connector-java-5.1.31-bin.jar /usr/share/java/mysql-connector-java.jar


##### Run /usr/bin/mysql_secure_installation to set the MySQL root password and other security-related settings.
/usr/bin/mysql_secure_installation 

##### Log in as the root user, or another user with privileges to create database and grant privileges:
mysql -u root -p

mysql> GRANT REPLICATION SLAVE ON *.* TO 'centos'@'ec2-52-59-211-4.eu-central-1.compute.amazonaws.com' IDENTIFIED BY 'password';

mysql> SET GLOBAL binlog_format = 'ROW'; 

mysql> FLUSH TABLES WITH READ LOCK;

##### create a database for cloudera
