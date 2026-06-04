DAY -02:
Linux fundamentals 

command to see the running process 
ps -ef | grep <service_name>   OR ps aux | grep <servicae_name>
for example 
ps -ef | grep java

in o/p will show the result some number , whixh is know as PID 

by refering the PID , we can suppose the service i srunning or not.
if need to kill the running process we , can use command 

kill -9 PID (forcefull deletion of running process)

for the resource utilization we can use the below commnds 

top - we cvan see the running process in the server and zobmie process too , with priority of service and change to renice the value
free -m - memory utilization  
swapon -s - to list all the active swap space dir/file
vmstat - virtual memory statistics (monitor swap using real time) 
iostat - statistics of uses ram , 
commands 
systemd 
commands
systemctl status <service_name>
systemctl start | stop | restart | enable | disable

eg. sysytemctl status name

command to install application 
apt update
apt install jenkins -y
to delete the application  command 
sudo apt remove jenkins 
to remove configuartion as well , we can command 
sudo apt purge jenkins 



