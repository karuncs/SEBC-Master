
##### mount and reserve space
 mount
 lsblk

 ##### network
 ifconfig

 ###### lookups
getent hosts xxxxxx

###### install packages
yum install -y bind-utils
yum install -y wget


##### check the swappiness on eachnode and set it to 1
        to check current swappiness: sysctl status vm.swappiness
		to make as 1: sudo sysctl vm.swappiness=1

#### mount attributes
    df -hT 
    
    findmnt

     cat /etc/fstab

######
Transparent Huge Page Compaction is enabled and can cause significant performance problems. Run 

 "echo never > /sys/kernel/mm/transparent_hugepage/defrag" and 

echo never > /sys/kernel/mm/transparent_hugepage/enabled" to disable this, 

 if the permission denied then try ..

sudo su -

echo never > /sys/kernel/mm/transparent_hugepage/defrag

echo never > /sys/kernel/mm/transparent_hugepage/enabled

and then add the same command to an init script such as /etc/rc.local so it will be set on system reboot. The following hosts are affected: 

sudo echo "never > /sys/kernel/mm/transparent_hugepage/enabled" >> /etc/rc.local
sudo echo "never > /sys/kernel/mm/transparent_hugepage/defrag" >> /etc/rc.local

##### Edit sudo vi /etc/sysconfig/network with the FQDN of corresponding host only
HOSTNAME=ec2-18-194-110-208.eu-central-1.compute.amazonaws.com

HOSTNAME=ec2-18-184-233-154.eu-central-1.compute.amazonaws.com

HOSTNAME=ec2-3-121-22-155.eu-central-1.compute.amazonaws.com

HOSTNAME=ec2-52-59-211-4.eu-central-1.compute.amazonaws.com

search eu-central-1.compute.internal eu-central-1.compute.amazonaws.com

nameserver 172.31.0.2

##### List forward and reverse host lookups using getent
getent hosts 18.194.110.208

18.194.110.208  ec2-18-194-110-208.eu-central-1.compute.amazonaws.com masterNode

 getent hosts 18.184.233.154

18.184.233.154  ec2-18-184-233-154.eu-central-1.compute.amazonaws.com secondaryMasterNode

getent hosts 3.121.22.155

3.121.22.155    ec2-3-121-22-155.eu-central-1.compute.amazonaws.com dataNode1

getent hosts 52.59.211.4

52.59.211.4     ec2-52-59-211-4.eu-central-1.compute.amazonaws.com dataNode2


#### yum utils

yum install -y yum-utils

##### Disabled SELinux
  sudo vi /etc/selinux/config
  
    SELinux=disabled
echo 0 > /sys/fs/selinux/enforce

###### firewall status
systemctl status firewalld.service 

systemctl status firewalld

###### iptables status

systemctl status iptable

##### check nscd status

  sudo yum install -y nscd

   sudo service nscd start

   sudo service nscd status

   ##### httpd
   sudo yum install -y httpd

sudo systemctl start httpd
systemctl status httpd

####check ntpd status

   sudo yum install -y ntp

   > sudo service ntpd start

   sudo service ntpd status

###### JDK installation and path setup

Download the jdk-8u162-linux-x64

rpm -ivh jdk-8u162-linux-x64.rpm

create bash profile 

# export Java in .bashfile
 vi ~/.bash_profile
export JAVA_HOME=/usr/java/jdk1.8.0_162
export PATH=$PATH:$JAVA_HOME\bin
source ~/.bash_profile
# check the java path is updated or not

echo $JAVA_HOME