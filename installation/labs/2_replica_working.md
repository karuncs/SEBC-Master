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

sudo yum install -y mysql


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

sudo tar zxvf mysql-connector-java-5.1.47.tar.gz

sudo mkdir -p /usr/share/java/

sudo cp mysql-connector-java-5.1.47/mysql-connector-java-5.1.47-bin.jar /usr/share/java/mysql-connector-java.jar




#Log in as the root user, or another user with privileges to create database and grant privileges:
mysql -u root -p
#create a database for cloudera
CREATE DATABASE hive DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
CREATE DATABASE oozie DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
CREATE DATABASE hue DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
CREATE DATABASE scm DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci; 
CREATE DATABASE sentry DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;
CREATE DATABASE rman DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;

GRANT ALL ON hive.* TO 'hive'@'%' IDENTIFIED BY 'Bootcamp';
GRANT ALL ON scm.* TO 'scm'@'%' IDENTIFIED BY 'Bootcamp';
GRANT ALL ON oozie.* TO 'oozie'@'%' IDENTIFIED BY 'Bootcamp';
GRANT ALL ON hue.* TO 'hue'@'%' IDENTIFIED BY 'Bootcamp';
GRANT ALL ON sentry.* TO 'amon'@'%' IDENTIFIED BY 'Bootcamp';
GRANT ALL ON rman.* TO 'rman'@'%' IDENTIFIED BY 'Bootcamp';

You can also confirm the privilege grants for a given user by running:
SHOW GRANTS FOR 'scm'@'%';
/usr/share/cmf/schema/scm_prepare_database.sh mysql scm scm Ace4ever
# give the access for databases
GRANT ALL ON <database>.* TO '<user>'@'%' IDENTIFIED BY '<password>'
# Run the scm_prepare_database.sh script on the host where the Cloudera Manager Server package is installed:

#/usr/share/cmf/schema/scm_prepare_database.sh database-type mysql database-name username password
/usr/share/cmf/schema/scm_prepare_database.sh mysql scm scm

## check the db version
SELECT VERSION();
SHOW VARIABLES LIKE "%version%";

mysql -u root -p -e 'SHOW VARIABLES LIKE "%version%";'

hostname : ip-172-31-44-83.eu-west-2.compute.internal

show databases;


chnage the hostname in db properties: vi /etc/cloudera-scm-server/db.properties