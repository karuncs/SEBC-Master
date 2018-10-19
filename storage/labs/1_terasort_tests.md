useradd karun
sudo -u hdfs hdfs dfs -mkdir -p /user/karun
sudo -u hdfs hdfs dfs -chown karun /user/karun
su - karun

sudo -u hdfs hdfs dfs -mkdir -p /user/raffles
sudo -u hdfs hdfs dfs -chown karun /user/raffles
sudo -u hdfs hdfs dfs -mkdir -p /user/fullerton
sudo -u hdfs hdfs dfs -chown karun /user/fullerton
su - raffles


time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapreduce.job.maps=4  -D dfs.blocksize=32M 100000000 /user/karun/teragen

time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort -Dmapred.map.tasks.speculative.execution=false /user/karun/teragen /user/karun/terasort
