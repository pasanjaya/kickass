#### file navigation
```
cd
ls , ls -a , ls -A, ls -l, ls -a -l, ls -A -l ,ls -a -l --color
mkdir , rmdir
rm , rm -rf
cp , mv (move and rename)

history
history -c
history -d <line number>
```
#### file manipulation
```
view - more, less, head, tail, cat
edit - vim, nano, gedit
create empty - touch
>>,>,|
&& - left after right
&  - left run on background
```

#### services
```
service --status-all
	+ running
	- not running
	? can not be determined (WTF services)
service <service name> start/stop/restart/reload/status
```
```
systemctl list-unit-files
	static
	enabled
	disabled

systemctl start/stop/restart/reload/status <service name>
```
#### explore services and process running on ports
```
*view services and ports
netstat -a	Everyting 
netstat -tulpn 	Active listening and Active listening
netstat -plnt   Only Listening


sudo lsof -i :<port number>     more details in NAME
sudo lsof -n -i :<port number>	less details in NAME
sudo lsof -t -i :<port number>	view only por numbers
```
#### process
```
top 
htop ( sudo apt-get install htop)

ps
ps -A
ps -le			(Ex - sudo ps -le | grep apache2)
	UID		- user identification number
	PID		- process identification number
	PPID	- parent process identification number
	PRI		- priority  of the process 
			PR is the process's actual priority that use by Linux kernel
					range - (0 , 139) 
					(0 to 99 for real time and 100 to 139 for users)
	NI		- nice value of the process
			In Linux we can set guidelines for the CPU to follow 
			when it is looking at all the tasks it has to do.
			These guidelines are called niceness or nice value
					range - (-20 to 19)
					* The lower the number the more priority that task gets
					* niceness value is high number like 19 the task will be set to the lowest priority 
          * -20 is highest, 0 default and +19 is lowest
          * PR = 20 + NI
          * default nice in /etc/security/limits.conf
	TTY		- terminal type
ps -p pid1,pid2,pid3....
ps -C <program or service or script name>
ps -G <group name>

*change nice value
nice -n <nice value> <process name> [Ex : nice -n 10 chrom]
renice <nice value> -p <pid>        [Ex : renice 10 -p $(pgrep apache2)]

*view 5 scheduling policies in a LINUX environment (IDK ,modify and apply those policies)
chart -m

pstree
pstree -a

pgrep <program or service or script name> (pgrep apache | wc -l)

kill    <pid>
pkill   <process name>
killall <process name>

cTrl + D (throw to background)
```
#### file system
```
* hard link
ln <source> <link>
rm <hard link>

* soft link
ln -s <source> <link>
rm <soft link>

#disk file system
df -h     - human readable
df -m     - in MB
df -i     - inode info
df -T     - file system type
df -t/-x <file type>    - include/exclude specific file system type
df -hT <directory>      - directory info

du -a -h <folder>  //disk usage free space

sudo fdisk -l - HDD info
sudo badblocks -v /dev/sda*
```
#### searching things
```
whereis - binary, source code, man page
which   - binary
locate  - 
find    -
```
#### utilities 
```
grep <reg expression> (sudo ps -le | grep apache2)

sort <file name>  (Ex sort foo.txt > sortfoo.txt)
sort -r <file name>
sort -n <fiile name> 
sort -n -r <file name>

wc -l   - lines
wc -w   - words
wc -m   - characters
```




