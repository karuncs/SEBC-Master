##### Edit sudo vi /etc/sysconfig/network with the FQDN of corresponding host only
HOSTNAME=ec2-18-194-110-208.eu-central-1.compute.amazonaws.com
HOSTNAME=ec2-18-184-233-154.eu-central-1.compute.amazonaws.com
HOSTNAME=ec2-3-121-22-155.eu-central-1.compute.amazonaws.com
HOSTNAME=ec2-52-59-211-4.eu-central-1.compute.amazonaws.com

##### test the connection/communication between servers/instances

     ssh -i xxxxx.pem centos@fqdn
     for instance: ssh -i ClouderaBootcampKey.pem centos@ec2-18-184-233-154.eu-central-1.compute.amazonaws.com
	  to make this work, get the pem file from aws and put it on all instances and change the permissions on each node
		chmod 400 ClouderaBootcampKey.pem


##### Disabled SELinux
  sudo vi /etc/selinux/config
    SELinux=disabled

#### mount attributes
    df -h 

###### firewall status
systemctl status firewalld.service 

######
Transparent Huge Page Compaction is enabled and can cause significant performance problems. Run 
"echo never > /sys/kernel/mm/transparent_hugepage/defrag" and 
echo never > /sys/kernel/mm/transparent_hugepage/enabled" to disable this, 

 if the permission denied then try ..

sudo su -
echo never > /sys/kernel/mm/transparent_hugepage/defrag
echo never > /sys/kernel/mm/transparent_hugepage/enabled

and then add the same command to an init script such as /etc/rc.local so it will be set on system reboot. The following hosts are affected: 
echo "never > /sys/kernel/mm/transparent_hugepage/enabled" >> /etc/rc.local
echo "never > /sys/kernel/mm/transparent_hugepage/defrag" >> /etc/rc.local

##### check nscd status
  sudo yum install -y nscd

   sudo service nscd start

   sudo service nscd status

####check ntpd status
   sudo yum install -y ntp

    sudo service ntpd start

   sudo service ntpd status

