
##### teragen command

time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapreduce.job.maps=6  -D dfs.blocksize=32M 51200000 /user/raffles/tgen512

##### output of time command

real    0m57.014s
user    1m9.988s
sys     0m4.437s

###### hdfs dfs -ls /user/raffles/tgen512

Found 2 items
-rw-r--r--   3 raffles supergroup          0 2018-10-19 09:08 /user/raffles/tgen512/_SUCCESS
-rw-r--r--   3 raffles supergroup 5120000000 2018-10-19 09:08 /user/raffles/tgen512/part-m-00000


time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort -Dmapred.map.tasks.speculative.execution=false /user/karun/teragen /user/karun/terasort
