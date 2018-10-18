```
add ......sentry.service.admin.group

cfusi
```

beeline
>!connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-44-83.eu-west-2.compute.internal@REALM.COM

SHOW TABLES;

0 tables

full trasactions.....

beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-44-83.eu-west-2.compute.internal@REALM.COM
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-44-83.eu-west-2.compute.internal@REALM.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables
. . . . . . . . . . . . . . . . . . . .> ;
INFO  : Compiling command(queryId=hive_20181018100202_04cb9639-c754-42d5-8ea9-befcc87e6436): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181018100202_04cb9639-c754-42d5-8ea9-befcc87e6436); Time taken: 0.686 seconds
INFO  : Executing command(queryId=hive_20181018100202_04cb9639-c754-42d5-8ea9-befcc87e6436): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181018100202_04cb9639-c754-42d5-8ea9-befcc87e6436); Time taken: 0.173 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (1.246 seconds)
0: jdbc:hive2://localhost:10000/default>


##### configure the hive server2 impersation

In beeline:
CREATE ROLE sentry_admin;
GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
GRANT ROLE sentry_admin TO GROUP {your_primary};

id in the linux terminal:  id cloudera-scm
id cloudera-scm
uid=997(cloudera-scm) gid=994(cloudera-scm) groups=994(cloudera-scm)

GRANT ROLE sentry_admin TO GROUP {cloudera-scm};


SHOW TABLES;
