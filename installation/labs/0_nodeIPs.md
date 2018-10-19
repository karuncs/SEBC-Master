#### Make proper hostnames.. good to have a hostname as fqdn
	sudo vi /etc/hostname

#### Make persistant hosts with fqdns and/or shortname(optional)
Cloud Provider: AWS cloud
Linux Release: hostnamectl
DiskSpace: df -h
List command output: yum repolist enabled

add users:
  * `$ sudo groupadd hotels`
    * `$ sudo groupadd shops`
    * `$ sudo useradd -u 2000 -g hotels raffles`
    * `$ sudo useradd -u 3000 -g shops fullerton`

	vi /etc/passwd
	vi /etc/group



##### test the connection/communication between servers/instances

     ssh -i xxxxx.pem centos@fqdn
     for instance: ssh -i ClouderaBootcampKey.pem centos@ip-172-31-38-68.eu-central-1.compute.internal
	  to make this work, get the pem file from aws and put it on all instances and change the permissions on each node
		sudo chmod 400 ClouderaBootcampKey.pem
