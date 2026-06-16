

# Day 06 – Linux Fundamentals: Read and Write Text Files

ubuntu@ip-172-31-36-132:~$ touch notes.txt
ubuntu@ip-172-31-36-132:~$ echo "this is milind" > notes.txt
ubuntu@ip-172-31-36-132:~$ cat no
node-js-sample/ notes.txt
ubuntu@ip-172-31-36-132:~$ cat notes.txt
this is milind
ubuntu@ip-172-31-36-132:~$ cat notes.txt >> notes.txt
cat: notes.txt: input file is output file
ubuntu@ip-172-31-36-132:~$ echo this is mac  >> notes.txt
ubuntu@ip-172-31-36-132:~$ cat notes.txt
this is milind
this is mac

ubuntu@ip-172-31-36-132:~$ echo "this is zanje family" | tee -a notes.txt
this is zanje family
ubuntu@ip-172-31-36-132:~$ cat notes.txt
this is milind
this is mac
this is zanje family
ubuntu@ip-172-31-36-132:~$

ubuntu@ip-172-31-36-132:~$ head -n 2 notes.txt
this is milind
this is mac
ubuntu@ip-172-31-36-132:~$ tail  -n 2 notes.txt
this is mac
this is zanje family

# user permission
ubuntu@ip-172-31-36-132:~$ ls -l notes.txt
-rw-rw-r-- 1 ubuntu docker 48 Jun 16 10:35 notes.txt
# Breakdown:
-rwxr-xr--
│││ │ │ └─ Others
│││ │ └── Group
│││ └──── Owner
│└└────── Permissions
└──────── File Type

# Permission Types
Symbol	Meaning	Numeric
r	Read	4
w	Write	2
x	Execute	1
# Permission Types
permission to groups 
User     rwx  : read write execute
group    rw_  : read write no execute
other    r    : read only 

#examples 
chmod 755 notes.txt

Owner  = rwx
Group  = r-x
Others = r-x

chmod +x script.sh

# change ownership 

chown 
example :
sudo chown ubuntu:devops file.txt|

ubuntu@ip-172-31-36-132:~$ stat notes.txt
  File: notes.txt
  size: 48        	Blocks: 8          IO Block: 4096   regular file
Device: 259,1	Inode: 291056      Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/  ubuntu)   Gid: ( 1004/  docker)
Access: 2026-06-16 10:36:01.841692850 +0000
Modify: 2026-06-16 10:35:55.213586589 +0000
Change: 2026-06-16 10:35:55.213586589 +0000
 Birth: 2026-06-16 10:33:19.738090249 +0000
