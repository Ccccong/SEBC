# 1. Check vm.swappiness on all your nodes Set the value to 1 if necessary
```
[root@ip-172-31-6-7 ~]# ./rallsh.sh "sysctl vm.swappiness"
cmd=- sysctl vm.swappiness -
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "sysctl vm.swappiness" 
vm.swappiness = 60
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "sysctl vm.swappiness" 
vm.swappiness = 60
[root@ip-172-31-6-7 ~]# ./rallsh.sh "sysctl vm.swappiness=1"
cmd=- sysctl vm.swappiness=1 -
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "sysctl vm.swappiness=1" 
vm.swappiness = 1
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "sysctl vm.swappiness=1" 
vm.swappiness = 1
```

# 2.Show the mount attributes of your volume(s)

Resize2fs /dev/xvde

[root@ip-172-31-6-7 ~]# mount -v|grep "on / "
```
/dev/xvde on / type ext4 (rw)

ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "df -v -m" 
Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/xvde          30238   655     28049   3% /
tmpfs               7506     0      7506   0% /dev/shm
```
# 3.If you have ext-based volumes, list the reserve space setting 
``` 
[root@ip-172-31-6-7 ~]# dumpe2fs /dev/xvde |more
dumpe2fs 1.41.12 (17-May-2010)
Filesystem volume name:   centos_root
Last mounted on:          /
Filesystem UUID:          44d27f92-d3df-4207-80ea-22830afccf03
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1966080
Block count:              7864320
Reserved block count:     393145
Free blocks:              5800759
Free inodes:              1882305
```
# 4.Disable transparent hugepage support
```
[root@ip-172-31-3-160 ~]#  cat /sys/kernel/mm/transparent_hugepage/enabled 
cat: /sys/kernel/mm/transparent_hugepage/enabled: No such file or directory
[root@ip-172-31-3-160 ~]# ls -l /sys/kernel/mm/
total 0
drwxr-xr-x. 3 root root 0 May  8 13:31 hugepages
drwxr-xr-x. 2 root root 0 May  8 13:31 ksm

[root@ip-172-31-3-160 ~]# cat /proc/meminfo | grep HugePages 
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
```
# 5.List your network interface configuration
```
[root@ip-172-31-6-7 ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 0A:76:D3:09:26:92  
          inet addr:172.31.6.7  Bcast:172.31.15.255  Mask:255.255.240.0
          inet6 addr: fe80::876:d3ff:fe09:2692/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62346 (60.8 KiB)  TX bytes:64882 (63.3 KiB)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13092 (12.7 KiB)  TX bytes:13092 (12.7 KiB)
```
# 6.Show that forward and reverse host lookups are correctly resolved
```
[root@ip-172-31-6-7 ~]# getent hosts
127.0.0.1       localhost.localdomain localhost
127.0.0.1       localhost6.localdomain6 localhost6
172.31.6.7       ip-172-31-6-7.ec2.internal	vm1
172.31.5.148    ip-172-31-5-148.ec2.internal  vm2
172.31.15.40    ip-172-31-15-40.ec2.internal	vm3
172.31.11.232   ip-172-31-11-232.ec2.internal vm4
172.31.6.212    ip-172-31-6-212.ec2.internal vm5

[root@ip-172-31-6-7 ~]# nslookup `hostname`
Server:         172.31.0.2
Address:        172.31.0.2#53

Non-authoritative answer:
Name:   ip-172-31-6-7.ec2.internal
Address: 172.31.6.7

```
# 7.Show the nscd service is running
```
[root@ip-172-31-6-7 ~]# rash "service nscd status"
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service nscd status" 
nscd (pid 4456) is running...
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service nscd status" 
nscd (pid 1038) is running...
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service nscd status" 
nscd (pid 4275) is running...
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service nscd status" 
nscd (pid 1036) is running...
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service nscd status" 
nscd (pid 1038) is running... 
```
# 8.Show the  ntpd  service is running
```
rash "yum -y install ntp"
rash "chkconfig ntpd on"
```
```
[root@ip-172-31-6-7 ~]# rash "service ntpd status"
Connect to vm1
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service ntpd status" 
ntpd (pid  4581) is running...
Connect to vm2
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service ntpd status" 
ntpd (pid  1114) is running...
Connect to vm3
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service ntpd status" 
ntpd (pid  4351) is running...
Connect to vm4
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service ntpd status" 
ntpd (pid  1112) is running...
Connect to vm5
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service ntpd status" 
ntpd (pid  1114) is running...
```
# 9. misc
1 stop selinux
```
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "cat /etc/selinux/config|grep ^SELINUX" 
SELINUX=disabled
```
```
[root@ip-172-31-6-7 ~]# rash getenforce
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "getenforce" 
Disabled
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "getenforce" 
Disabled
```
2 stop iptables
```
[root@ip-172-31-6-7 ~]# ./rallsh.sh "chkconfig iptables off"
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "chkconfig iptables off" 
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "chkconfig iptables off" 

[root@ip-172-31-6-7 ~]# ./rallsh.sh "service iptables stop"
ssh -i  AWS-SEBC-TRAINING.pem root@vm1 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm2 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm3 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm4 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
ssh -i  AWS-SEBC-TRAINING.pem root@vm5 "service iptables stop" 
iptables: Setting chains to policy ACCEPT: filter [  OK  ]
iptables: Flushing firewall rules: [  OK  ]
iptables: Unloading modules: [  OK  ]
```






