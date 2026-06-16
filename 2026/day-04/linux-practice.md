Process checks
ps

ps -ef | grep <service_name>

Service checks

commands :
systemctl status jenkins

systemctl stop jenkins
systemctl start jenkins
systemctl restart jenkins
systemctl enable jenkins
systemctl disable jenkins

systemctl list-units

LOG checks :
commands:

journalctl -u <service_name>

ubuntu@ip-172-31-36-132:~$ sudo journalctl -u docker | head 
Jun 13 19:04:43 ip-172-31-36-132 systemd[1]: Starting docker.service - Docker Application Container Engine...
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.453068745Z" level=info msg="Starting up"
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.454187530Z" level=info msg="OTEL tracing is not configured, using no-op tracer provider"
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.454501230Z" level=info msg="CDI directory does not exist, skipping: failed to monitor for changes: no such file or directory" dir=/etc/cdi
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.454610076Z" level=info msg="CDI directory does not exist, skipping: failed to monitor for changes: no such file or directory" dir=/var/run/cdi
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.454814752Z" level=info msg="detected 127.0.0.53 nameserver, assuming systemd-resolved, so using resolv.conf: /run/systemd/resolve/resolv.conf"
Jun 13 19:04:43 ip-172-31-36-132 dockerd[2156]: time="2026-06-13T19:04:43.514620565Z" level=info msg="Creating a containerd client" address=/run/containerd/containerd.sock timeout=1m0s


2) 
ubuntu@ip-172-31-36-132:~$ sudo journalctl -u docker | tail -f
Jun 14 03:39:21 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:21.970213789Z" level=info msg="image created" imageID="sha256:d7186bd20ef60b2bcc0c8fe9085b6e08940be77a7dd0c9e7705f23532c9caca0" tag="moby-dangling@sha256:d7186bd20ef60b2bcc0c8fe9085b6e08940be77a7dd0c9e7705f23532c9caca0"
Jun 14 03:39:22 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:22.412203835Z" level=info msg="image created" imageID="sha256:984173da34859805f9504200fb42123b62c1d102cb5d4c8fa3c7bba25ae7af19" tag="moby-dangling@sha256:984173da34859805f9504200fb42123b62c1d102cb5d4c8fa3c7bba25ae7af19"
Jun 14 03:39:22 ip-172-31-36-132 dockerd[2682]: time="20

4) grep command 
buntu@ip-172-31-36-132:~$ grep milind  /etc/passwd 
milind:x:1001:1002::/home/milind:/bin/sh


buntu@ip-172-31-36-132:~$ grep milind  /etc/passwd 
milind:x:1001:1002::/home/milind:/bin/sh

tail command :
ubuntu@ip-172-31-36-132:~$ getent group | tail 
tcpdump:x:985:
landscape:x:106:
fwupd-refresh:x:984:
polkitd:x:983:
admin:x:107:
netdev:x:108:
ubuntu:x:1000:
docker:x:109:ubuntu
zanje:x:1001:milind
milind:x:1002:


GROUP in lINUX 


# command to create a group 
ubuntu@ip-172-31-36-132:~$ sudo groupadd devops
# check the existance of group 
ubuntu@ip-172-31-36-132:~$ getent group devops
devops:x:1003:
or cat /etc/group
# check group of specific user 
ubuntu@ip-172-31-36-132:~$ groups ubuntu
ubuntu : ubuntu adm cdrom sudo dip lxd docker

ubuntu@ip-172-31-36-132:~$ id ubuntu
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),102(lxd),109(docker)

# add user to group 
ubuntu@ip-172-31-36-132:~$ groups ubuntu
ubuntu : ubuntu adm cdrom sudo dip lxd docker

ubuntu@ip-172-31-36-132:~$ gpasswd -a ubuntu docker 
gpasswd: Permission denied.

ubuntu@ip-172-31-36-132:~$ sudo gpasswd -a ubuntu docker 
Adding user ubuntu to group docker
ubuntu@ip-172-31-36-132:~$ 
# add user to multiple group 

ubuntu@ip-172-31-36-132:~$ sudo usermod -aG docker,sudo,devops ubuntu

ubuntu@ip-172-31-36-132:~$ id ubuntu
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),102(lxd),109(docker),1003(devops)

# delete group 
command :
groupdel devops

ubuntu@ip-172-31-36-132:~$ sudo groupdel devops
ubuntu@ip-172-31-36-132:~$ getent devops
Unknown database: devops
Try `getent --help' or `getent --usage' for more information.
ubuntu@ip-172-31-36-132:~$ grep devops /etc/group
ubuntu@ip-172-31-36-132:~$ grep zanje /etc/group
zanje:x:1001:milind

# again add and see the group 

ubuntu@ip-172-31-36-132:~$ sudo addgroup devops
ubuntu@ip-172-31-36-132:~$ grep devops /etc/group
devops:x:1003:


# milind troubleshooting 
milind is not present as sudo group 

groups milind
ubuntu@ip-172-31-36-132:~$ sudo usermod -aG sudo milind
ubuntu@ip-172-31-36-132:~$ groups milind
milind : milind zanje sudo
ubuntu@ip-172-31-36-132:~$ groups milind
milind : milind zanje sudo
ubuntu@ip-172-31-36-132:~$ groups sudo
groups: 'sudo': no such user
ubuntu@ip-172-31-36-132:~$ groups ubuntu
ubuntu : ubuntu adm cdrom dip lxd docker
# to refresh the added group : command :

newgrp <service_name>

ubuntu@ip-172-31-36-132:~$ newgrp docker
ubuntu@ip-172-31-36-132:~$ sudo usermod -aG docker ubuntu
ubuntu@ip-172-31-36-132:~$ groups ubuntu
ubuntu : ubuntu adm cdrom dip lxd docker




