###### Rename the cluster

Cluster name: Challenge
api call: --2018-10-19 08:47:17--  http://ec2-35-177-37-181.eu-west-2.compute.amazonaws.com:7180/api/v14/hosts
Resolving ec2-35-177-37-181.eu-west-2.compute.amazonaws.com (ec2-35-177-37-181.eu-west-2.compute.amazonaws.com)... 172.31.36.142
Connecting to ec2-35-177-37-181.eu-west-2.compute.amazonaws.com (ec2-35-177-37-181.eu-west-2.compute.amazonaws.com)|172.31.36.142|:7180.


###### output of the user command
sudo -u hdfs hdfs dfs -mkdir -p /user/raffles
sudo -u hdfs hdfs dfs -chown karun /user/raffles
sudo -u hdfs hdfs dfs -mkdir -p /user/fullerton
sudo -u hdfs hdfs dfs -chown karun /user/fullerton
su - raffles

hdfs dfs -ls /user


`
Found 7 items
drwxr-xr-x   - admin  admin               0 2018-10-19 08:38 /user/admin
drwxr-xr-x   - hdfs   supergroup          0 2018-10-19 08:51 /user/fullerton
drwxrwxrwx   - mapred hadoop              0 2018-10-19 08:27 /user/history
drwxrwxr-t   - hive   hive                0 2018-10-19 08:28 /user/hive
drwxrwxr-x   - hue    hue                 0 2018-10-19 08:28 /user/hue
drwxrwxr-x   - oozie  oozie               0 2018-10-19 08:29 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2018-10-19 08:50 /user/raffle

`