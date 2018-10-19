
sudo -u hdfs hdfs dfs -mkdir -p /user/raffles
sudo -u hdfs hdfs dfs -chown karun /user/fullerton
su - karun


time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapreduce.job.maps=6  -D dfs.blocksize=32M 51200000 /user/raffles/tgen512

time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort -Dmapred.map.tasks.speculative.execution=false /user/karun/teragen /user/karun/terasort
