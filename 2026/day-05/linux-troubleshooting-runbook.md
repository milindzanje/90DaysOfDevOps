
# Target service / process
ubuntu@ip-172-31-36-132:~$ uname -a
Linux ip-172-31-36-132 7.0.0-1006-aws #6-Ubuntu SMP PREEMPT Tue May 26 12:04:34 UTC 2026 x86_64 GNU/Linux
ubuntu@ip-172-31-36-132:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 26.04 LTS
Release:	26.04
Codename:	resolute
ubuntu@ip-172-31-36-132:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 26.04 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo
  
# Snapshot: CPU & Memory

mkdir /tmp/runbook-demo, cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo


ubuntu@ip-172-31-36-132:~$ cat /tmp/runbook-demo/
cat: /tmp/runbook-demo/: Is a directory
ubuntu@ip-172-31-36-132:~$ cat /tmp/runbook-demo/hosts-copy
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


# Snapshot: Disk & IO

ubuntu@ip-172-31-36-132:~$ df -kh
Filesystem       Size  Used Avail Use% Mounted on
/dev/root         15G  4.0G   11G  28% /
tmpfs            455M     0  455M   0% /dev/shm
tmpfs            182M  1.1M  181M   1% /run
efivarfs         128K  3.1K  120K   3% /sys/firmware/efi/efivars
tmpfs            455M  4.0K  455M   1% /tmp
/dev/nvme0n1p13  989M   96M  827M  11% /boot
/dev/nvme0n1p15  105M  6.3M   99M   7% /boot/efi
none             1.0M     0  1.0M   0% /run/credentials/getty@tty1.service
none             1.0M     0  1.0M   0% /run/credentials/serial-getty@ttyS0.service
none             1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
none             1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
none             1.0M     0  1.0M   0% /run/credentials/systemd-networkd.service
tmpfs             91M  8.0K   91M   1% /run/user/1000
ubuntu@ip-172-31-36-132:~$ free -m
               total        used        free      shared  buff/cache   available
Mem:             908         450         174           2         415         458
Swap:              0           0           0


untu@ip-172-31-36-132:~$ df -T | head
Filesystem      Type     1K-blocks    Used Available Use% Mounted on
/dev/root       ext4      15067780 4101056  10950340  28% /
tmpfs           tmpfs       465264       0    465264   0% /dev/shm
tmpfs           tmpfs       186108    1044    185064   1% /run
efivarfs        efivarfs       128       4       120   3% /sys/firmware/efi/efivars
tmpfs           tmpfs       465264       4    465260   1% /tmp
/dev/nvme0n1p13 ext4       1012140   97548    845832  11% /boot
/dev/nvme0n1p15 vfat        106832    6414    100418   7% /boot/efi
none            tmpfs         1024       0      1024   0% /run/credentials/getty@tty1.service
none            tmpfs         1024       0      1024   0% /run/credentials/serial-getty@ttyS0.service
ubuntu@ip-172-31-36-132:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 1  0      0 178080  23592 403336    0    0    16    22   88    0  0  0 100  0  0  0
ubuntu@ip-172-31-36-132:~$ iostat
Linux 7.0.0-1006-aws (ip-172-31-36-132) 	06/16/26 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.07    0.00    0.03    0.02    0.05   99.83

Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
loop0             0.00         0.00         0.00         0.00        820          0          0
loop1             0.00         0.00         0.00         0.00        510          0          0
loop2             0.00         0.13         0.00         0.00      29378          0          0
loop3             0.00         0.00         0.00         0.00         14          0          0
nvme0n1           0.94        16.38        22.18         0.00    3736554    5058994          0
# Snapshot: Network

buntu@ip-172-31-36-132:~$ netstat -tulnp
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:41961         0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.54:53           0.0.0.0:*               LISTEN      -
tcp6       0      0 :::3000                 :::*                    LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
udp        0      0 127.0.0.1:323           0.0.0.0:*                           -
udp        0      0 127.0.0.54:53           0.0.0.0:*                           -
udp        0      0 127.0.0.53:53           0.0.0.0:*                           -
udp        0      0 172.31.36.132:68        0.0.0.0:*                           -
udp6       0      0 ::1:323                 :::*                                -
ubuntu@ip-172-31-36-132:~$ netstat -tulnp | grep 8080
(No info could be read for "-p": geteuid()=1000 but you should be root.)
ubuntu@ip-172-31-36-132:~$ netstat -tulnp | grep 8080
(No info could be read for "-p": geteuid()=1000 but you should be root.)
ubuntu@ip-172-31-36-132:~$ sudo lsof -i :8080
ubuntu@ip-172-31-36-132:~$ sudo lsof -i :3000
COMMAND    PID USER FD   TYPE DEVICE SIZE/OFF NODE NAME
docker-pr 8088 root 7u  IPv4  37162      0t0  TCP *:3000 (LISTEN)
docker-pr 8094 root 7u  IPv6  37163      0t0  TCP *:3000 (LISTEN)

# Logs reviewed
ubuntu@ip-172-31-36-132:~$ journalctl -u docker  -n 5
Jun 14 03:39:28 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:28.451965509Z" level=info msg="i>
Jun 14 03:39:29 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:29.008438670Z" level=info msg="i>
Jun 14 03:39:29 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:29.559601630Z" level=info msg="i>
Jun 14 03:39:29 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:39:29.616788247Z" level=info msg="i>
Jun 14 03:40:59 ip-172-31-36-132 dockerd[2682]: time="2026-06-14T03:40:59.400793236Z" level=info msg="s>
lines 1-5/5 (END)

# Quick findings

ubuntu@ip-172-31-36-132:~$ ps -ef | grep docker
root        2682       1  0 Jun13 ?        00:00:27 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
root        8088    2682  0 Jun14 ?        00:00:00 /usr/bin/docker-proxy -proto tcp -host-ip 0.0.0.0 -host-port 3000 -container-ip 172.17.0.2 -container-port 3000 -use-listen-fd
root        8094    2682  0 Jun14 ?        00:00:00 /usr/bin/docker-proxy -proto tcp -host-ip :: -host-port 3000 -container-ip 172.17.0.2 -container-port 3000 -use-listen-fd
ubuntu     20130   19745  0 10:24 pts/1    00:00:00 grep --color=auto docker
ubuntu@ip-172-31-36-132:~$ curl http://localhost:3000
curl: (56) Recv failure: Connection reset by peer
ubuntu@ip-172-31-36-132:~$ curl ifconfig.me
44.251.46.247ubuntu@ip-172-31-36-132:~$
^C
ubuntu@ip-172-31-36-132:~$ telnet google.com 80
Trying 142.250.69.174...
Connected to google.com.
Escape character is '^]'.

^C
Connection closed by foreign host.
ubuntu@ip-172-31-36-132:~$ telnet 172.31.36.132 8080
Trying 172.31.36.132...
telnet: Unable to connect to remote host: Connection refused
ubuntu@ip-172-31-36-132:~$ telnet localhost  8080
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
ubuntu@ip-172-31-36-132:~$ telnet 172.31.36.132 3000
Trying 172.31.36.132...
telnet: Unable to connect to remote host: Connection refused
ubuntu@ip-172-31-36-132:~$ nc -zv
usage: nc [-46CDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl]
	  [-m minttl] [-O length] [-P proxy_username] [-p source_port]
	  [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit]
	  [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]]
	  [destination] [port]
ubuntu@ip-172-31-36-132:~$ nc -zv 8.8.8.8 80
^C
ubuntu@ip-172-31-36-132:~$ nc -zv 172.31.36.132 8080
nc: connect to 172.31.36.132 port 8080 (tcp) failed: Connection refused

ubuntu@ip-172-31-36-132:~$ nc -zv google.com 443
Connection to google.com (142.250.69.174) 443 port [tcp/https] succeeded!
# If this worsens (next steps)
