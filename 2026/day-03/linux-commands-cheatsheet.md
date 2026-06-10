Process management

top
ps 
ps -ef 
ps aux | grep <service_name>
ps -ef | grep java



File system

/bin : essentials users command binaries like cat , ls ,zcat , vi , 
/boot : static files of bootloader , including Linx kernel (like vmlinux-7 * * )
/dev  : Essentials device nodes kile /dev/sda 
/etc  : host specific system wide configuration files like /etc/host . /etc/resolve.cong , 
/home : home directories 
/media : mount points for media like usb , cd-rom
/mnt: mount point for temporarily mounting  file system manually 
/opt : add on application software package
/proc : process , virtual file system to provide as process and kernel as file like cpu , memory 
/root : superuser dir 
/run : runtime variable data
/sbin : essential system binaries like fsck , reboot 
/sys : info about kernel filesyaytem and hardware
/tmp : tempo files that delete after reboot
/usr : user info read only user data , containint application and libraries 
/var : Variable data files such as system logs , spool dir ,


Networking troubleshooting
for networking trouble shooting
commnads 
ping to remote host
ping 8.8.8.8 -t

to see port connectivity in application
netsta -tulnp | grep 8080


telnet command to see the hops 
 * specific service is running and accessible behind a firewall.
 
telnet google.com 80

telnet mail.example.com 25 
telnet 10.1.1.1 22 

DNS & DNS Records 
command 
nslookup google.com


