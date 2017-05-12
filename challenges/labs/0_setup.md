# List the cloud provider you are using (AWS, GCE, Azure, other)   
```
AWS
```
# List the nodes you are using by IP address and name
```
ec2-54-197-9-181.compute-1.amazonaws.com		ip-172-31-1-9.ec2.internal	172.31.1.9	
ec2-54-165-195-53.compute-1.amazonaws.com		ip-172-31-12-204.ec2.internal	172.31.12.204	
ec2-54-162-212-249.compute-1.amazonaws.com			ip-172-31-1-94.ec2.internal	172.31.1.94	
ec2-54-152-227-138.compute-1.amazonaws.com		ip-172-31-6-28.ec2.internal	172.31.6.28	
ec2-107-23-188-175.compute-1.amazonaws.com	ip-172-31-6-145.ec2.internal	172.31.6.145    
```

# List the Linux release you are using
```
CentOS-6.5
```
```
uname -a
Linux ip-172-31-1-9 2.6.32-431.el6.x86_64 #1 SMP Fri Nov 22 03:15:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

# Demonstrate the disk capacity available on each node is >= 30 GB
```
Connect to ip-172-31-1-9.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-9.ec2.internal "df -v -k|grep xvde" 
/dev/xvde       30963708 669892  28721236   3% /

Connect to ip-172-31-12-204.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-12-204.ec2.internal "df -v -k|grep xvde" 
/dev/xvde       30963708 671256  28719872   3% /

Connect to ip-172-31-1-94.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-94.ec2.internal "df -v -k|grep xvde" 
/dev/xvde       30963708 670032  28721096   3% /

Connect to ip-172-31-6-28.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-28.ec2.internal "df -v -k|grep xvde" 
/dev/xvde       30963708 669668  28721460   3% /

Connect to ip-172-31-6-145.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-145.ec2.internal "df -v -k|grep xvde" 
/dev/xvde       30963708 669668  28721460   3% /

```

# List the command and output for  yum repolist enabled 
```
[root@ip-172-31-1-9 ~]#  yum repolist enabled 
Loaded plugins: fastestmirror, presto
Determining fastest mirrors
 * base: repos-va.psychz.net
 * extras: repo1.ash.innoscale.net
 * updates: mirror.math.princeton.edu
repo id                                                                              repo name                                                                                        status
base                                                                                 CentOS-6 - Base                                                                                  6,706
extras                                                                               CentOS-6 - Extras                                                                                   64
updates                                                                              CentOS-6 - Updates                                                                                 270
repolist: 7,040
```

# List the  /etc/passwd  entries for  cate  and  jemaine 
```
[root@ip-172-31-1-9 ~]# ./rallsh.sh "cat /etc/passwd|grep zhou"
Connect to ip-172-31-1-9.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-9.ec2.internal "cat /etc/passwd|grep zhou" 
zhou:x:2800:2800::/home/zhou:/bin/bash

Connect to ip-172-31-12-204.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-12-204.ec2.internal "cat /etc/passwd|grep zhou" 
zhou:x:2800:2800::/home/zhou:/bin/bash

Connect to ip-172-31-1-94.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-94.ec2.internal "cat /etc/passwd|grep zhou" 
zhou:x:2800:2800::/home/zhou:/bin/bash

Connect to ip-172-31-6-28.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-28.ec2.internal "cat /etc/passwd|grep zhou" 
zhou:x:2800:2800::/home/zhou:/bin/bash

Connect to ip-172-31-6-145.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-145.ec2.internal "cat /etc/passwd|grep zhou" 
zhou:x:2800:2800::/home/zhou:/bin/bash

[root@ip-172-31-1-9 ~]# ./rallsh.sh "cat /etc/passwd|grep chen"
Connect to ip-172-31-1-9.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-9.ec2.internal "cat /etc/passwd|grep chen" 
chen:x:2900:2900::/home/chen:/bin/bash

Connect to ip-172-31-12-204.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-12-204.ec2.internal "cat /etc/passwd|grep chen" 
chen:x:2900:2900::/home/chen:/bin/bash

Connect to ip-172-31-1-94.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-94.ec2.internal "cat /etc/passwd|grep chen" 
chen:x:2900:2900::/home/chen:/bin/bash

Connect to ip-172-31-6-28.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-28.ec2.internal "cat /etc/passwd|grep chen" 
chen:x:2900:2900::/home/chen:/bin/bash

Connect to ip-172-31-6-145.ec2.internal
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-145.ec2.internal "cat /etc/passwd|grep chen" 
chen:x:2900:2900::/home/chen:/bin/bash

```

# List the  /etc/group  entries for   shanghai    and   beijing  
Shanghai group info:
```
[root@ip-172-31-1-9 ~]# ./rallsh.sh "cat /etc/group|grep shanghai"
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-9.ec2.internal "cat /etc/group|grep shanghai" 
shanghai:x:2901:chen

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-12-204.ec2.internal "cat /etc/group|grep shanghai" 
shanghai:x:2901:chen

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-94.ec2.internal "cat /etc/group|grep shanghai" 
shanghai:x:2901:chen

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-28.ec2.internal "cat /etc/group|grep shanghai" 
shanghai:x:2901:chen

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-145.ec2.internal "cat /etc/group|grep shanghai" 
shanghai:x:2901:chen
```
Beijing group info:
```
[root@ip-172-31-1-9 ~]# ./rallsh.sh "cat /etc/group|grep beijing"
ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-9.ec2.internal "cat /etc/group|grep beijing" 
beijing:x:2902:zhou

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-12-204.ec2.internal "cat /etc/group|grep beijing" 
beijing:x:2902:zhou

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-1-94.ec2.internal "cat /etc/group|grep beijing" 
beijing:x:2902:zhou

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-28.ec2.internal "cat /etc/group|grep beijing" 
beijing:x:2902:zhou

ssh -i  AWS-SEBC-TRAINING.pem root@ip-172-31-6-145.ec2.internal "cat /etc/group|grep beijing" 
beijing:x:2902:zhou

```
