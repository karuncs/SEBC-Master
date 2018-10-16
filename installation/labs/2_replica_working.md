##### install Mysql database 5.7 version

###### MasterSQL....
the host here is: ec2-52-59-211-4.eu-central-1.compute.amazonaws.com

wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm

rpm -ivh mysql-community-release-el7-5.noarch.rpm

yum update

yum install mysql-server

systemctl start mysqld

##### Run /usr/bin/mysql_secure_installation to set the MySQL root password and other security-related settings.
/usr/bin/mysql_secure_installation 

##### on all nodes

yum install -y mysql


#####  to stop MySQl server if it running mysql
systemctl stop mysqld

##### Ensuer that Mysql start as a root
systemctl enable mysqld

##### create a user and grant permissions

mysql>create user 'repl'@'ec2-18-184-233-154.eu-central-1.compute.amazonaws.com' identified by 'Bootcamp';

mysql>grant replication slave on *.* to 'repl'@'ec2-18-184-233-154.eu-central-1.compute.amazonaws.com';

mysql>SET GLOBAL binlog_format = 'ROW'; 

mysql> FLUSH TABLES WITH READ LOCK;

##### do same on replicate server means another host
the replication host is: ec2-18-184-233-154.eu-central-1.compute.amazonaws.com

mysql -u root -p

##### download and copy JDBC driver on all nodes

Install the JDBC driver on the Cloudera Manager Server host, as well as any other hosts running services that require database access.

download the pltform independent jdbc driver from : https://dev.mysql.com/downloads/connector/j/5.1.html

tar zxvf mysql-connector-java-5.1.47.tar.gz

mkdir -p /usr/share/java/


cp mysql-connector-java-5.1.47/mysql-connector-java-5.1.47-bin.jar /usr/share/java/mysql-connector-java.jar


