#### Make proper hostnames.. good to have a hostname as fqdn
	sudo vi /etc/hostname

#### Make persistant hosts with fqdns and/or shortname(optional)
Take internal Ip and domain names



172.31.32.43 ip-172-31-32-43.eu-central-1.compute.internal Master

172.31.40.51 ip-172-31-40-51.eu-central-1.compute.internal SecondaryMasterNoe

172.31.33.225 ip-172-31-33-225.eu-central-1.compute.internal DataNode1

172.31.36.19 ip-172-31-36-19.eu-central-1.compute.internal DataNode2


external 

18.194.110.208 ec2-18-194-110-208.eu-central-1.compute.amazonaws.com masterNode

18.184.233.154 ec2-18-184-233-154.eu-central-1.compute.amazonaws.com secondaryMasterNode

3.121.22.155  ec2-3-121-22-155.eu-central-1.compute.amazonaws.com  dataNode1

52.59.211.4 ec2-52-59-211-4.eu-central-1.compute.amazonaws.com dataNode2



##### test the connection/communication between servers/instances

     ssh -i xxxxx.pem centos@fqdn
     for instance: ssh -i ClouderaBootcampKey.pem centos@ec2-18-184-233-154.eu-central-1.compute.amazonaws.com
	  to make this work, get the pem file from aws and put it on all instances and change the permissions on each node
		chmod 400 ClouderaBootcampKey.pem
