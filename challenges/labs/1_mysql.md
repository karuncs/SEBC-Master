###### hostname 
  ip-172-31-36-142.eu-west-2.compute.internal

###### DB Version
SHOW VARIABLES LIKE "%version%";

`
+-------------------------+------------------------------+
| Variable_name           | Value                        |
+-------------------------+------------------------------+
| innodb_version          | 5.6.41                       |
| protocol_version        | 10                           |
| slave_type_conversions  |                              |
| version                 | 5.6.41                       |
| version_comment         | MySQL Community Server (GPL) |
| version_compile_machine | x86_64                       |
| version_compile_os      | Linux                        |
+-------------------------
`
##### List of databases

show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
