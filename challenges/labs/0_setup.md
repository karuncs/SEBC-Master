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


##### 	vi /etc/passwd
	raffles:x:2000:1002::/home/raffles:/bin/bash
    fullerton:x:3000:1003::/home/fullerton:/bin/bash

##### 	vi /etc/group

	hotels:x:1002:
    shops:x:1003: