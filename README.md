# Project-Assignments

https://devopsrealtime.com/fun-with-linux-for-cloud-devops-engineers/ 

 

 

 

Pre-Requisites 

Login to AWS cloud and create Linux based EC2 instance to complete the below assignment. 

Deployment 

Login to the server as super user and perform below 

Create users and set passwords – user1, user2, user3 

Create Groups – devops, aws 

Change primary group of user2, user3 to ‘devops’ group 

Add ‘aws’ group as secondary group to the ‘user1’ 

Create the file and directory structure shown in the above diagram. 

Change group of /dir1, /dir7/dir10, /f2 to “devops” group 

Change ownership of /dir1, /dir7/dir10, /f2 to “user1” user. 

[ec2-user@ip-172-31-35-242 ~]$ sudo su - 

[root@ip-172-31-35-242 ~]# yum update -y 

Loaded plugins: extras_suggestions, langpacks, priorities, update-motd 

amzn2-core                                                                                                                                                            | 3.7 kB  00:00:00 

No packages marked for update 

[root@ip-172-31-35-242 ~]# useradd user1 

[root@ip-172-31-35-242 ~]# useradd user2 

[root@ip-172-31-35-242 ~]# useradd user3 

[root@ip-172-31-35-242 ~]# passwd user1 

Changing password for user user1. 

New password: 

Retype new password: 

passwd: all authentication tokens updated successfully. 

[root@ip-172-31-35-242 ~]# groupadd devops 

[root@ip-172-31-35-242 ~]# groupadd aws 

Cat /etc/group 

 

[root@ip-172-31-35-242 ~]# id -a 

uid=0(root) gid=0(root) groups=0(root) 

[root@ip-172-31-35-242 ~]# id -a user1 

uid=1001(user1) gid=1001(user1) groups=1001(user1) 

[root@ip-172-31-35-242 ~]# id -a user2 

uid=1002(user2) gid=1002(user2) groups=1002(user2) 

[root@ip-172-31-35-242 ~]# id -a user3 

uid=1003(user3) gid=1003(user3) groups=1003(user3) 

Change primary group of user2, user3 to ‘devops’ group 

 

[root@ip-172-31-35-242 ~]# usermod  -g devops user3 

[root@ip-172-31-35-242 ~]# id -a user3 

uid=1003(user3) gid=1004(devops) groups=1004(devops) 

[root@ip-172-31-35-242 ~]# usermod  -g devops user2 

[root@ip-172-31-35-242 ~]# id -a user2 

uid=1002(user2) gid=1004(devops) groups=1004(devops) 

Add ‘aws’ group as secondary group to the ‘user1’ 

[root@ip-172-31-35-242 ~]# usermod -a -G aws user1 

[root@ip-172-31-35-242 ~]# id -a user1 

uid=1001(user1) gid=1001(user1) groups=1001(user1),1005(aws) 

[root@ip-172-31-35-242 ~]# cd ~ 

[root@ip-172-31-35-242 ~]# pwd 

/root 

[root@ip-172-31-35-242 ~]# 

[root@ip-172-31-35-242 /]# mkdir {dir1,dir6} 

drwxr-xr-x   2 root root    6 Nov 26 09:06 dir6 

drwxr-xr-x   2 root root    6 Nov 26 09:06 dir1 

dr-xr-xr-x  20 root root  281 Nov 26 09:06 .. 

dr-xr-xr-x  20 root root  281 Nov 26 09:06 . 

[root@ip-172-31-35-242 /]# 

[root@ip-172-31-35-242 /]# touch /dir1/f1 

[root@ip-172-31-35-242 /]# ls -ltra /dir1/f1 

-rw-r--r-- 1 root root 0 Nov 26 09:06 /dir1/f1 

[root@ip-172-31-35-242 /]# ls -ld /dir2/dir1/dir2/dir10 

drwxr-xr-x 2 root root 6 Nov 26 09:08 /dir2/dir1/dir2/dir10 

[root@ip-172-31-35-242 /]# touch /dir2/dir1/dir2/f3 

[root@ip-172-31-35-242 /]# ls -ld /dir2/dir1/dir2/f3 

-rw-r--r-- 1 root root 0 Nov 26 09:09 /dir2/dir1/dir2/f3 

[root@ip-172-31-35-242 /]# mkdir -p dir3/dir11 

[root@ip-172-31-35-242 /]# ls -ld dir3/dir11 

drwxr-xr-x 2 root root 6 Nov 26 09:10 dir3/dir11 

[root@ip-172-31-35-242 /]# mkdir -p /dir4/dir12 

[root@ip-172-31-35-242 /]# touch /dir4/dir12/f4 

[root@ip-172-31-35-242 /]# touch /dir4/dir12/f5 

[root@ip-172-31-35-242 /]# mkdir -p /dir5/dir13 

[root@ip-172-31-35-242 /]# mkdir -p /dir5/dir13 

[root@ip-172-31-35-242 /]# mkdir -p /dir7/dir10 

[root@ip-172-31-35-242 /]# touch /dir7/f3 

[root@ip-172-31-35-242 /]# ls -ld /dir7/f3 

-rw-r--r-- 1 root root 0 Nov 26 09:14 /dir7/f3 

[root@ip-172-31-35-242 /]# mkdir -p /dir8/dir9 

[root@ip-172-31-35-242 /]# pwd 

/ 

[root@ip-172-31-35-242 /]# touch f1 f2 

[root@ip-172-31-35-242 /]# mkdir -p /opt/dir14/dir10 

[root@ip-172-31-35-242 /]# touch /opt/dir14/f3 

Change group of /dir1, /dir7/dir10, /f2 to “devops” group 

[root@ip-172-31-35-242 /]# ls -ltra /dir1/ 

total 4 

-rw-r--r--  1 root devops    0 Nov 26 09:06 f1 

drwxr-xr-x  2 root root     16 Nov 26 09:06 . 

dr-xr-xr-x 26 root root   4096 Nov 26 09:16 .. 

 

[root@ip-172-31-35-242 /]# chgrp -R devops /dir1 

[root@ip-172-31-35-242 /]# ls -ld /dir1 

drwxr-xr-x 2 root devops 16 Nov 26 09:06 /dir1 

[root@ip-172-31-35-242 /]# ls -ltra /dir1/f1 

-rw-r--r-- 1 root devops 0 Nov 26 09:06 /dir1/f1 

[root@ip-172-31-35-242 /]# pwd 

[root@ip-172-31-35-242 /]# chgrp devops f2 

[root@ip-172-31-35-242 /]# chown user1:devops f2 

 

Change group of /dir1, /dir7/dir10, /f2 to “devops” group 

Change ownership of /dir1, /dir7/dir10, /f2 to “user1” user. 

[root@ip-172-31-35-242 /]# chown -R user1:devops /dir1 

[root@ip-172-31-35-242 /]# ls -ltr /dir1 

total 0 

-rw-r--r-- 1 user1 devops 0 Nov 26 09:06 f1 

[root@ip-172-31-35-242 /]# ls -ld dir1 

drwxr-xr-x 2 user1 devops 16 Nov 26 09:06 dir1 

[root@ip-172-31-35-242 /]# chown -R user1:devops /dir7 

[root@ip-172-31-35-242 /]# ls -ltr /dir7/ 

total 0 

drwxr-xr-x 2 user1 devops 6 Nov 26 09:14 dir10 

-rw-r--r-- 1 user1 devops 0 Nov 26 09:14 f3 

 

Login as user1 and perform below 

Create users and set passwords – user4, user5 

Create Groups – app, database 

 

[root@ip-172-31-35-242 ssh]# vi sshd_config 

[root@ip-172-31-35-242 ssh]# pwd 

/etc/ssh 

[root@ip-172-31-35-242 ssh]# diff sshd_config sshd_config_bkp 

63c63 

< PasswordAuthentication yes 

--- 

> PasswordAuthentication no 

  97  systemctl stop sshd 

   98  systemctl status sshd 

   99  systemctl start sshd 

  100  systemctl status sshd 

login as: user1 

Server refused our key 

user1@18.217.24.90's password: 

  

       __|  __|_  ) 

       _|  (     /   Amazon Linux 2 AMI 

      ___|\___|___| 

  

https://aws.amazon.com/amazon-linux-2/ 

[user1@ip-172-31-35-242 ~]$ bash 

[user1@ip-172-31-35-242 ~]$ ls -ltra 

total 12 

-rw-r--r-- 1 user1 user1 231 Jul 15  2020 .bashrc 

-rw-r--r-- 1 user1 user1 193 Jul 15  2020 .bash_profile 

-rw-r--r-- 1 user1 user1  18 Jul 15  2020 .bash_logout 

drwx------ 2 user1 user1  62 Nov 26 08:29 . 

drwxr-xr-x 6 root  root   61 Nov 26 08:30 .. 

[user1@ip-172-31-35-242 ~]$ 

 

--> update VISUDO file with user1 under root priviliges 

## Allow root to run any commands anywhere 

root    ALL=(ALL)       ALL 

user1   ALL=(ALL) ALL 

[user1@ip-172-31-35-242 ~]$ useradd user4 

bash: /usr/sbin/useradd: Permission denied 

[user1@ip-172-31-35-242 ~]$ sudo useradd user4 

[sudo] password for user1: 

[user1@ip-172-31-35-242 ~]$ ls -ltr /home/ 

total 0 

drwx------ 3 ec2-user ec2-user 74 Nov 26 08:21 ec2-user 

drwx------ 2 user2    devops   62 Nov 26 08:30 user2 

drwx------ 2 user3    devops   62 Nov 26 08:30 user3 

drwx------ 2 user1    user1    83 Nov 26 09:50 user1 

drwx------ 2 user4    user4    62 Nov 26 09:53 user4 

drwx------ 2 user5    user5    62 Nov 26 09:55 user5 

[user1@ip-172-31-35-242 ~]$ 

[user1@ip-172-31-35-242 ~]$ sudo groupadd app 

[user1@ip-172-31-35-242 ~]$ sudo groupadd database 

app:x:1008: 

database:x:1009: 

[user1@ip-172-31-35-242 ~]$ cat /etc/group 

Login as ‘user4’ and perform below 

Create directory – /dir6/dir4 

Create file – /f3 

Move the file from “/dir1/f1” to “/dir2/dir1/dir2” 

Rename the file ‘/f2′ to /f4’ 

sudo  mkdir -p /dir6/dir4 

    8  ls -ltr /dir6/dir4 

    9  ls -ld /dir6/dir4 

15  touch f4 

   16  sudo touch f4 

sudo mv f1 /dir2/dir1/dir2 

   29  ls -ltr 

   30  ls -ltr /dir2/dir1/dir2 

 

Login as ‘user1’ and perform below 

Create directory – “/home/user2/dir1” 

Change to “/dir2/dir1/dir2/dir10” directory and create file “/opt/dir14/dir10/f1” using relative path method. 

Move the file from “/opt/dir14/dir10/f1” to  user1 home directory 

Delete the directory recursively “/dir4” 

Delete all child files and directories under “/opt/dir14” using single command. 

Write this text “Linux assessment for an DevOps Engineer!! Learn with Fun!!” to the /f3 file and save it. 

 

 

[user1@ip-172-31-35-242 dir10]$ touch /opt/dir14/dir10/f1 

touch: cannot touch ‘/opt/dir14/dir10/f1’: Permission denied 

[user1@ip-172-31-35-242 dir10]$ sudo touch /opt/dir14/dir10/f1 

[user1@ip-172-31-35-242 dir10]$ ls -ltr /opt/dir14/dir10/f1 

-rw-r--r-- 1 root root 0 Nov 26 10:35 /opt/dir14/dir10/f1 

[user1@ip-172-31-35-242 dir10]$ ls -ltr /opt/dir14/dir10/f1 

-rw-r--r-- 1 root root 0 Nov 26 10:35 /opt/dir14/dir10/f1 

 

[user1@ip-172-31-35-242 dir10]$ sudo mv /opt/dir14/dir10/f1 /home/user1 

[user1@ip-172-31-35-242 dir10]$ ls -ltr /home/user1/ 

total 0 

-rw-r--r-- 1 root root 0 Nov 26 10:35 f1 

[user1@ip-172-31-35-242 /]$ sudo rm -rf /dir4 

[user1@ip-172-31-35-242 /]$ cd /opt/dir14/ 

[user1@ip-172-31-35-242 dir14]$ sudo rm -r * 

[user1@ip-172-31-35-242 dir14]$ ls -ltr 

total 0 

[user1@ip-172-31-35-242 dir14]$ sudo vi f3 

[user1@ip-172-31-35-242 dir14]$ ls -ltr 

total 4 

-rw-r--r-- 1 root root 59 Nov 26 10:48 f3 

[user1@ip-172-31-35-242 dir14]$ cat f3 

Linux assessment for an DevOps Engineer!! Learn with Fun!! 

[user1@ip-172-31-35-242 dir14]$ pwd 

/opt/dir14 

 

Login as ‘user2’ and perform below 

Create file “/dir1/f2” 

Delete /dir6 

Delete /dir8 

Replace the “DevOps” text to “devops” in the /f3 file without using  editor. 

Using Vi-Editor copy the line1 and paste 10 times in the file /f3. 

Search for the pattern “Engineer” and replace with “engineer” in the file /f3 using single command. 

Delete /f3 

login as: user2 

Server refused our key 

user2@18.217.24.90's password: 

Access denied 

user2@18.217.24.90's password: 

Last failed login: Fri Nov 26 11:06:04 UTC 2021 from 122.171.198.231 on ssh:nott                                                                                                             y 

There was 1 failed login attempt since the last successful login. 

  

       __|  __|_  ) 

       _|  (     /   Amazon Linux 2 AMI 

      ___|\___|___| 

  

https://aws.amazon.com/amazon-linux-2/ 

[user2@ip-172-31-35-242 ~]$ bash 

[user2@ip-172-31-35-242 ~]$ id 

uid=1002(user2) gid=1004(devops) groups=1004(devops) 

[user2@ip-172-31-35-242 ~]$ 

[user2@ip-172-31-35-242 ~]$ sudo touch /dir1/f2 

[sudo] password for user2: 

[user2@ip-172-31-35-242 ~]$ ls -ld /dir1/f2 

-rw-r--r-- 1 root root 0 Nov 26 11:14 /dir1/f2 

 

[user2@ip-172-31-35-242 /]$ sudo rm -rf /dir6 /dir8 

[user2@ip-172-31-35-242 dir14]$ sudo sed 's/DevOps/devops/' f3 

Linux assessment for an devops Engineer!! Learn with Fun!! 

[user2@ip-172-31-35-242 dir14]$ cat f3 

Linux assessment for an DevOps Engineer!! Learn with Fun!! 

[user2@ip-172-31-35-242 dir14]$ sudo sed 's/DevOps/devops' f3 

sed: -e expression #1, char 15: unterminated `s' command 

[user2@ip-172-31-35-242 dir14]$ sudo sed 'S/DevOps/devops' f3 

sed: -e expression #1, char 1: unknown command: `S' 

[user2@ip-172-31-35-242 dir14]$ sudo sed 's/DevOps/devops/' f3 

Linux assessment for an devops Engineer!! Learn with Fun!! 

[user2@ip-172-31-35-242 dir14]$ vi f3 

[user2@ip-172-31-35-242 dir14]$ sudo vi f3 

[user2@ip-172-31-35-242 dir14]$ cat /f3 

[user2@ip-172-31-35-242 dir14]$ sudo cat f3 

[sudo] password for user2: 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

Linux assessment for an DevOps Engineer!! Learn with Fun! 

[user2@ip-172-31-35-242 dir14]$ sudo sed 's/Engineer/engineer/g' f3 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

Linux assessment for an DevOps engineer!! Learn with Fun! 

 

 

Login as ‘root’ user and perform below 

Search for the file name ‘f3’ in the server and list all obsolete paths where f3 file is found. 

[root@ip-172-31-35-242 /]# find . -name f3 

./dir2/dir1/dir2/f3 

./dir7/f3 

./f3 

 

Show the count of the number of files in the directory ‘/’ 

[root@ip-172-31-35-242 /]# ls -l | wc -l 

29 

 

Print last line of the file ‘/etc/passwd’ 

[user2@ip-172-31-35-242 dir14]$ tail -1 /etc/passwd 

user5:x:1005:1007::/home/user5:/bin/bash 

Login to AWS and create 5GB EBS volume in the same AZ of the EC2 instance and attach EBS volume to the Instance. 

 

 

 

Login as ‘root’user and perform below 

Create File System on the new EBS volume attached in the previous step 

Mount the File System on /data directory 

Verify File System utilization using ‘df -h’ command – This command must show /data file system 

Create file ‘f1’ in the /data file system. 

 

  lsblk -f 

  mkfs -t ext4 /dev/xvdf 

  mkdir /data 

 mount /dev/xvdf /data 

 

[root@ip-172-31-35-242 ~]# df -h 

Filesystem      Size  Used Avail Use% Mounted on 

devtmpfs        474M     0  474M   0% /dev 

tmpfs           483M     0  483M   0% /dev/shm 

tmpfs           483M  404K  483M   1% /run 

tmpfs           483M     0  483M   0% /sys/fs/cgroup 

/dev/xvda1      8.0G  1.6G  6.5G  19% / 

tmpfs            97M     0   97M   0% /run/user/1000 

/dev/xvdf       4.8G   20M  4.6G   1% /data 

 

[root@ip-172-31-35-242 data]# ls -ltr /data/f1 

-rw-r--r-- 1 root root 0 Nov 26 17:46 /data/f1 

userdel user1 

  165  userdel user2 

  166  groupdel aws 

  167  groupdel devops 

  168  userdel user3 

  169  userdel user2 

  170  userdel user3 

  171  userdel user4 

  172  userdel user5 

  173  [root@ip-172-31-35-242 data]# ls -ltr /data/f1 

  174  -rw-r--r-- 1 root root 0 Nov 26 17:46 /data/f1 

  175  userdel user5 

  176  groupdel aws devops 

  177  groupdel app 

  178  groupdel database 

  179  cat /etc/groups 

  180  cat /etc/group 

  181  cd /home 

  182  ls -ltr 

  183  rm -r user1 

  184  sudo rm -rf user* 

  185  ls -ltr 

  186  df -h 

  187  umount /data 

  188  df -h 

  189  sudo rm -r /data 

Login to AWS and detach EBS volume to the EC2 Instance and delete the volume and then terminate EC2 instance. 

 

 

 

 

 

 

 
