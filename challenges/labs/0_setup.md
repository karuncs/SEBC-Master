#### Make persistant hosts with fqdns and/or shortname(optional)
Cloud Provider: AWS cloud

Linux Release: hostnamectl

###### DiskSpace
 
 server1

 Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.2G   99G   2% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           7.8G   17M  7.8G   1% /run
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000


server2


Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.2G   99G   2% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           7.8G   17M  7.8G   1% /run
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000


server3

Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      100G  1.2G   99G   2% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           7.8G   17M  7.8G   1% /run
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000


###### List command output: yum repolist enabled

Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.vooservers.com
 * extras: mirrors.vooservers.com
 * updates: mirrors.vooservers.com
repo id                             repo name                             status
!base/7/x86_64                      CentOS-7 - Base                       9,911
!extras/7/x86_64                    CentOS-7 - Extras                       432
!updates/7/x86_64                   CentOS-7 - Updates                    1,561
repolist: 11,904



####  add users:
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