https://www.cloudera.com/documentation/enterprise/5-13-x/topics/sg_self_signed_tls.html
certificate for only cloudera manager


mkdir -p /opt/cloudera/security/x509/ /opt/cloudera/security/jks/

$ sudo chown -R cloudera-scm:cloudera-scm /opt/cloudera/security/jks
$ sudo umask 0700
$ cd /opt/cloudera/security/jks

keytool -genkeypair -alias cmhost -keyalg RSA -keysize 2048 -dname "cn=ip-172-31-44-83.eu-west-2.compute.internal, ou=Department, o=Company, l=City, st=State, c=US" -keypass password -keystore example.jks -storepass password

sudo cp $JAVA_HOME/jre/lib/security/cacerts $JAVA_HOME/jre/lib/security/jssecacerts

keytool -export -alias cmhost -keystore example.jks -rfc -file /opt/cloudera/security/jks/selfsigned.cer

cp selfsigned.cer /opt/cloudera/security/x509/cmhost.pem

keytool -import -alias cmhost -file /opt/cloudera/security/jks/selfsigned.cer -keystore $JAVA_HOME/jre/lib/security/jssecacerts -storepass changeit

 mv /opt/cloudera/security/jks/example.jks /opt/cloudera/security/jks/cmhost-keystore.jks


 next part

 https://www.cloudera.com/documentation/enterprise/5-13-x/topics/how_to_configure_cm_tls.html#xd_583c10bfdbd326ba-7dae4aa6-147c30d0933--7a61


 kerberos....

 setup kerbros
 https://gist.github.com/ashrithr/4767927948eca70845db
 https://blog.puneethabm.com/configure-hadoop-security-with-cloudera-manager-using-kerberos/


 install on cm:  yum install openldap-clients
 install on all nodes: 
 yum install -y krb5-workstation

 https://gist.github.com/ashrithr/4767927948eca70845db

 sudo yum -y install krb5-server krb5-libs

 edit /etc/krb5.conf

 # Configuration snippets may be placed in this directory as well
includedir /etc/krb5.conf.d/

[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 dns_lookup_realm = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 rdns = false
 default_realm = BOOTCAMP.COM
 default_ccache_name = KEYRING:persistent:%{uid}

[realms]
# EXAMPLE.COM = {
#  kdc = kerberos.example.com
#  admin_server = kerberos.example.com
# }

[domain_realm]
 .bootcamp.com = BOOTCAMP.COM
 bootcamp.com = BOOTCAMP.COM

.......................................

 vi /var/kerberos/krb5kdc/kdc.conf
default_realm = BOOTCAMP.COM
[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
 BOOTCAMP.COM = {
  #master_key_type = aes256-cts
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
  supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal camellia256-cts:normal camellia128-cts:normal des-hmac-sha1:normal des-cbc-md5:normal des-cbc-crc:normal
 }


vi /var/kerberos/krb5kdc/kadm5.acl
*/admin@BOOTCAMP.COM    *


Creating KDC database to hold our sensitive Kerberos data
kdb5_util create -r BOOTCAMP.COM -s

Now on the KDC create a admin principal and also a test user (user1):
>kadmin.local
kadmin.local:  addprinc root/admin
kadmin.local:  addprinc user1
kadmin.local:  ktadd -k /var/kerberos/krb5kdc/kadm5.keytab kadmin/admin
kadmin.local:  ktadd -k /var/kerberos/krb5kdc/kadm5.keytab kadmin/changepw
kadmin.local:  exit


Let’s start the Kerberos KDC and kadmin daemons:

systemctl start krb5kdc.service
systemctl start kadmin.service
systemctl enable krb5kdc.service
systemctl enable kadmin.service


Now, let’s create a principal for our KDC server and stick it in it’s keytab:

[root@kdc ~]# kadmin.local
kadmin.local:  addprinc -randkey host/kdc.cw.com
kadmin.local:  ktadd host/kdc.cw.com


kadmin.local 

modify_principal +allow_renewable -maxrenewlife 7day HTTP/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day HTTP/ip-172-31-35-31.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day HTTP/ip-172-31-35-54.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day HTTP/ip-172-31-38-8.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day HTTP/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day K/M@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day cloudera-scm@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hdfs/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hdfs/ip-172-31-35-31.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hdfs/ip-172-31-38-8.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hdfs/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hive/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day httpfs/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day hue/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day kadmin/admin@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day kadmin/changepw@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day kadmin/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day kiprop/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day krbtgt/BOOTCAMP.COM@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day mapred/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day oozie/ip-172-31-35-54.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day yarn/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day yarn/ip-172-31-38-8.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day zookeeper/ip-172-31-35-155.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day zookeeper/ip-172-31-35-31.eu-west-2.compute.internal@BOOTCAMP.COM
modify_principal +allow_renewable -maxrenewlife 7day zookeeper/ip-172-31-44-83.eu-west-2.compute.internal@BOOTCAMP.COM