http://www.oschina.net/translate/20-advanced-commands-for-linux-experts?cmp&p=2#
解释管理 Linux 服务器所需的一些命令。 

# 41. 命令: ifconfig

ifconfig用来配置常驻内核的网络接口信息。在系统启动必要时用来设置网络适配器的信息。之后，它通常是只需要在调试时或当系统需要调整时使用。

## 检查活动网络适配器

```
[avishek@tecmint ~]$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 40:2C:F4:EA:CF:0E  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
```

## 检查所有的网络适配器

“-a”参数用来显示所有网络适配器(网卡)的详细信息,包括那些停用的适配器。

```
[avishek@tecmint ~]$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 40:2C:F4:EA:CF:0E  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
```

## 停用网络适配器

```
[avishek@tecmint ~]$ ifconfig eth0 down
```
## 启用网络适配器

```
[avishek@tecmint ~]$ ifconfig eth0 up
```
## 指定IP地址到网络适配器

为网络适配器eth0设定IP地址“192.168.1.12”.

```
[avishek@tecmint ~]$ ifconfig eth0 192.168.1.12
```
## 更改网络适配器eth0的子网掩码

```
[avishek@tecmint ~]$ ifconfig eth0 netmask 255.255.255.
```
## 更改网络适配器eth0的广播地址

```
[avishek@tecmint ~]$ ifconfig eth0 broadcast 192.168.1.255
```
## 为网络适配器eth0指定IP地址,子网掩码，广播地址

```
[avishek@tecmint ~]$ ifconfig eth0 192.168.1.12 netmask 255.255.255.0 broadcast 192.168.1.255
```
注Note: 如果你设置一块无线网卡的信息,你可以使用的命令是“iwconfig”.欲知更多ifconfig命令的例子和使用方法，读“15个有用的ifconfig 命令”. 
http://www.tecmint.com/ifconfig-command-examples/



# 42. 命令: netstat

netstat命令显示各种网络相关的信息，如网络连接,路由表,接口统计,伪装连接,组播成员身份等....

## 列出所有的网络端口

```
[avishek@tecmint ~]$ netstat -a

Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     741379   /run/user/user1/keyring-I5cn1c/gpg
....
```

## 显示所有tcp相关端口

```
[avishek@tecmint ~]$ netstat -at

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:5901                  *:*                     LISTEN     
tcp        0      0 *:5902                  *:*                     LISTEN     
...
```

## 显示所有连接的统计信息

```
[avishek@tecmint ~]$ netstat -s

Ip:
    4994239 total packets received
    0 forwarded
    0 incoming packets discarded
    4165741 incoming packets delivered
    3248924 requests sent out
    8 outgoing packets dropped
Icmp:
    29460 ICMP messages received
    566 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 98
....
```

## 不解析netstat 输出的主机、端口和用户名称 。

```
[avishek@tecmint ~]$ netstat -an

激活Internet连接 (服务器和已建立连接的)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     
tcp        1      0 192.168.1.218:52616     45.55.41.223:80         CLOSE_WAIT 
tcp6       0      0 :::80                   :::*                    LISTEN     
udp        0      0 0.0.0.0:42915           0.0.0.0:*                                  
活跃的UNIX域套接字 (服务器和已建立连接的)
Proto RefCnt Flags       Type       State         I-Node   路径
unix  2      [ ACC ]     流        LISTENING     21451    /home/omcube/.gnupg/S.gpg-agent
unix  2      [ ACC ]     流        LISTENING     24602    @/tmp/.ICE-unix/2023

```

## 获取 netstat 持续输出的动态信息，通过传递中断输出指令 (ctrl + c)来停止。

```
[avishek@tecmint ~]$ netstat -c
```

更多关于“netstat”的例子和使用方法，浏览文章“20个netstat 的使用案例”。 
http://www.tecmint.com/20-netstat-commands-for-linux-network-management/




# 43. 命令： nslookup

网络实用程序，用于获得互联网服务器的信息。顾名思义，该实用程序将发现通过查询 DNS 域的名称服务器信息。

```
[avishek@tecmint ~]$ nslookup tecmint.com 

Server:		192.168.1.1 
Address:	192.168.1.1#53 

Non-authoritative answer: 
Name:	tecmint.com 
Address: 50.16.67.239
```
## 查询 邮件 交换器 记录

```
[avishek@tecmint ~]$ nslookup -query=mx tecmint.com 

Server:		192.168.1.1 
Address:	192.168.1.1#53 

Non-authoritative answer: 
tecmint.com	mail exchanger = 0 smtp.secureserver.net. 
tecmint.com	mail exchanger = 10 mailstore1.secureserver.net. 

Authoritative answers can be found from:
```

## 查询域名服务器

```
[avishek@tecmint ~]$ nslookup -type=ns tecmint.com 

Server:		192.168.1.1 
Address:	192.168.1.1#53 

Non-authoritative answer: 
tecmint.com	nameserver = ns3404.com. 
tecmint.com	nameserver = ns3403.com. 

Authoritative answers can be found from:
```

## 查询DNS记录

```
[avishek@tecmint ~]$ nslookup -type=any tecmint.com 

Server:		192.168.1.1 
Address:	192.168.1.1#53 

Non-authoritative answer: 
tecmint.com	mail exchanger = 10 mailstore1.secureserver.net. 
tecmint.com	mail exchanger = 0 smtp.secureserver.net. 
tecmint.com	nameserver = ns06.domaincontrol.com. 
tecmint.com	nameserver = ns3404.com. 
tecmint.com	nameserver = ns3403.com. 
tecmint.com	nameserver = ns05.domaincontrol.com. 

Authoritative answers can be found from:
```

## 查询 起始 授权机构

```
[avishek@tecmint ~]$ nslookup -type=soa tecmint.com 

Server:		192.168.1.1 
Address:	192.168.1.1#53 

Non-authoritative answer: 
tecmint.com 
	origin = ns3403.hostgator.com 
	mail addr = dnsadmin.gator1702.hostgator.com 
	serial = 2012081102 
	refresh = 86400 
	retry = 7200 
	expire = 3600000 
	minimum = 86400 

Authoritative answers can be found from:
```

## 查询端口号

更改使用你想要连接的端口号

```
[avishek@tecmint ~]$ nslookup -port 56 tecmint.com

Server:		tecmint.com
Address:	50.16.76.239#53

Name:	56
Address: 14.13.253.12
```
更多阅读 8个Nslookup 命令 
http://www.tecmint.com/8-linux-nslookup-commands-to-troubleshoot-dns-domain-name-server/




# 44. 命令: dig

dig是查询DNS 域名服务器的工具，可以查询的主机地址、 邮件交流、 域名服务器相关的信息。在任何 Linux (Unix) 或 Macintosh OS X 操作系统上，都可以使用该工具。dig的最典型的用法是单个主机的查询。

```
[avishek@tecmint ~]$ dig tecmint.com

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com 
;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<
```

## 关闭注释行

```
[avishek@tecmint ~]$ dig tecmint.com +nocomments 

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com +nocomments 
;; global options: +cmd 
;tecmint.com.			IN	A 
tecmint.com.		14400	IN	A	40.216.66.239 
;; Query time: 418 msec 
;; SERVER: 192.168.1.1#53(192.168.1.1) 
;; WHEN: Sat Jun 29 13:53:22 2013 
;; MSG SIZE  rcvd: 45
```

## 关闭认证块

```
[avishek@tecmint ~]$ dig tecmint.com +noauthority 

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com +noauthority 
;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<
```

## 关闭 其他 块

```
[avishek@tecmint ~]$ dig  tecmint.com +noadditional 

; <<>> DiG 9.9.2-P1 <<>> tecmint.com +noadditional
;; global options: +cmd
;; Got answer:
;; ->>HEADER<
```

## 关闭 统计块

```
[avishek@tecmint ~]$ dig tecmint.com +nostats 

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com +nostats 
;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<
```

## 关闭回复块

```
[avishek@tecmint ~]$ dig tecmint.com +noanswer 

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com +noanswer 
;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<
```

## 关闭所有块

```
[avishek@tecmint ~]$ dig tecmint.com +noall 

; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.17.rc1.el6 <<>> tecmint.com +noall 
;; global options: +cmd
```
阅读更多10 个Linux Dig 命令实例 
http://www.tecmint.com/10-linux-dig-domain-information-groper-commands-to-query-dns/


# 45.命令: uptime

你连接到你的 Linux 服务器时发现一些不寻常或恶意的东西，你会做什么？
你可以运行uptime来验证当服务器无人值守式到底发生了什么事情。

```
[avishek@tecmint ~]$ uptime

14:37:10 up  4:21,  2 users,  load average: 0.00, 0.00, 0.04
```

# 46. 命令: wall

对系统管理员来说一个最重要的命令.wall发送一条消息到大家登录端, 将其 mesg 权限设置为"yes"。这条信息可以被wall作为参数，或者可以将它作为wall的标准输入。

```
[avishek@tecmint ~]$ wall "we will be going down for maintenance for one hour sharply at 03:30 pm"

Broadcast message from root@localhost.localdomain (pts/0) (Sat Jun 29 14:44:02 2013): 

we will be going down for maintenance for one hour sharply at 03:30 pm
```


# 47. 命令: mesg

其他人们可以使用"wtrite"命令,您发送文本到屏幕上。你可以控制是否显示。

```
mesg [n|y] n - prevents the message from others popping up on the screen. y – Allows messages to appear on your screen.
```

# 48. 命令: write

如果 'mesg' 是 'y'，让你的文本直接发送到另一台 Linux 机器的屏幕。.

```
[avishek@tecmint ~]$ write ravisaive
```

# 49. 命令: talk

增强的write命令，talk命令可让你与其他登录的用户交谈。

```
[avishek@tecmint ~]$ talk ravisaive
```

注释: 如果 talk 命令没安装的话,可以通过apt 或yum 安装所需的包.

```
[avishek@tecmint ~]$ yum install talk
OR
[avishek@tecmint ~]$ apt-get install talk
```


# 50. 命令：w

是否觉得命令'w'很滑稽？但是事实上不是的。它是一个命令，尽管只有一个字符长！命令"w"是uptime和who命令，以前后的顺序组合在一起。

```
[avishek@tecmint ~]$ w

15:05:42 up  4:49,  3 users,  load average: 0.02, 0.01, 0.00 
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT 
server   tty7     :0               14:06    4:43m  1:42   0.08s pam: gdm-passwo 
server   pts/0    :0.0             14:18    0.00s  0.23s  1.65s gnome-terminal 
server   pts/1    :0.0             14:47    4:43   0.01s  0.01s bash
```

# 51. 命令: rename

见名知意，这个命令重命名文件。rename将会通过从文件名的首字符开始替换，重命名为指定的文件名。

Give the file names a1, a2, a3, a4.....1213

仅仅写这些命令：[@Lesus 注： 在Ubuntu上不支持这种格式， rename与mv不同的是，rename可以批量修改，如同带了while的mv操作。]

 rename a1 a0 a?
 rename a1 a0 a??


# 52. 命令: top

显示CPU进程信息。这个命令自动刷新，默认是持续显示CPU进程信息，除非使用了中断指令。

```
[avishek@tecmint ~]$ top

top - 14:06:45 up 10 days, 20:57,  2 users,  load average: 0.10, 0.16, 0.21
Tasks: 240 total,   1 running, 235 sleeping,   0 stopped,   4 zombie
%Cpu(s):  2.0 us,  0.5 sy,  0.0 ni, 97.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   2028240 total,  1777848 used,   250392 free,    81804 buffers
KiB Swap:  3905532 total,   156748 used,  3748784 free,   381456 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+ COMMAND                                                                                                            
23768 ravisaiv  20   0 1428m 571m  41m S   2.3 28.9  14:27.52 firefox                                                                                                            
24182 ravisaiv  20   0  511m 132m  25m S   1.7  6.7   2:45.94 plugin-containe                                                                                                    
26929 ravisaiv  20   0  5344 1432  972 R   0.7  0.1   0:00.07 top                                                                                                                
24875 ravisaiv  20   0  263m  14m  10m S   0.3  0.7   0:02.76 lxterminal                                                                                                         
    1 root      20   0  3896 1928 1228 S   0.0  0.1   0:01.62 init                                                                                                               
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.06 kthreadd                                                  
```
另查看 12 TOP命令例子 ·[@Lesus 注：htop比top命令更好用，不过需要自己安装] 
http://www.tecmint.com/12-top-command-examples-in-linux/


# 53. 命令: mkfs.ext4

这个命令在指定的设备上创建一个新的ext4文件系统，如果这个命令后面跟的是个错误的设备，那么整个设备就会被擦除和格式化，所以建议不要运行这个命令，除非你清楚自己正在干什么。

Mkfs.ext4 /dev/sda1 (sda1 block will be formatted)
mkfs.ext4 /dev/sdb1 (sdb1 block will be formatted)

更多查看： Ext4是什么及怎么创建和转换 
http://www.tecmint.com/what-is-ext2-ext3-ext4-and-how-to-create-and-convert-linux-file-systems/


# 54. vi/emac/nano 命令

vi (visual), emac, nano 是 linux 中最常用的一些编辑器。它们经常用于编辑文本，配置,… 等文件. A quick guide to work around vi and nano is, emac is a.

## vi 编辑器：

```
[avishek@tecmint ~]$ touch a.txt (创建一个名为a.txt的文本文件) 
[avishek@tecmint ~]$ vi a.txt (用vi打开a.txt)
```
[按下‘i’键进入插入模式, 否则你不能输入任何内容]

echo "Hello"  (这里的文本会存到文件中)

    alt+x (退出插入模式, 记得在最后的字符间留有一些空格.
    ctrl+x 命令或你上一个单词将被删除).
    :wq! (以当前的文本保存文件, 记住‘!’ 是覆盖的意思).

# nano 编辑器：

```
[avishek@tecmint ~]$ nano a.txt (用nano打开 a.txt)
```
edit, with the content, required

ctrl +x (关闭编辑器).它会显示如下的提示输出信息:

Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?                    
 Y Yes 
 N No           ^C Cancel

点击‘y’ 选择 yes 并输入文件名,就完成编辑了. 


# 55. 命令: rsync

Rsync复制文件，参数-P开启进度条。如果你已经安装了rsync，你可以使用一个简单的别名。

alias cp='rsync -aP'

现在尝试在终端复制一个大文件，这样将会看到显示剩余部分的输出，与进度条类似。

而且，保持和维护备份是系统管理员不得不做的最重要、最无聊的工作之一。Rsync是一个用于新建和维护备份的非常好用的终端工具（也存在许多其它工具）。

```
[avishek@tecmint ~]$ rsync -zvr IMG_5267\ copy\=33\ copy\=ok.jpg ~/Desktop/ 

sending incremental file list 
IMG_5267 copy=33 copy=ok.jpg 

sent 2883830 bytes  received 31 bytes  5767722.00 bytes/sec 
total size is 2882771  speedup is 1.00
```
注意: -z表示压缩， -v表示详细信息，-r表示递归。 



# 56. 命令: free

跟踪内存的使用和资源一样重要，就像管理员执行的任何其它任务，可以使用 'free' 命令来在这里救援.
当前内存使用状态Current Usage Status of Memory

```
[avishek@tecmint ~]$ free

             total       used       free     shared    buffers     cached
Mem:       2028240    1788272     239968          0      69468     363716
-/+ buffers/cache:    1355088     673152
Swap:      3905532     157076    3748456
```
设置输出单位为KB，MB或GB

```
[avishek@tecmint ~]$ free -b

             total       used       free     shared    buffers     cached
Mem:    2076917760 1838272512  238645248          0   71348224  372670464
-/+ buffers/cache: 1394253824  682663936
Swap:   3999264768  160845824 3838418944
```
```
[avishek@tecmint ~]$ free -k

             total       used       free     shared    buffers     cached
Mem:       2028240    1801484     226756          0      69948     363704
-/+ buffers/cache:    1367832     660408
Swap:      3905532     157076    3748456
```
```
[avishek@tecmint ~]$ free -m

             total       used       free     shared    buffers     cached
Mem:          1980       1762        218          0         68        355
-/+ buffers/cache:       1338        641
Swap:         3813        153       3660
```
```
[avishek@tecmint ~]$ free -g

             total       used       free     shared    buffers     cached
Mem:             1          1          0          0          0          0
-/+ buffers/cache:          1          0
Swap:            3          0          3
```
以可读的格式显示，检查当前内存使用

```
[avishek@tecmint ~]$ free -h

             total       used       free     shared    buffers     cached
Mem:          1.9G       1.7G       208M         0B        68M       355M
-/+ buffers/cache:       1.3G       632M
Swap:         3.7G       153M       3.6G
```
设定 时间间隔 后 ，持续检查 使用状态

```
[avishek@tecmint ~]$ free -s 3

             total       used       free     shared    buffers     cached
Mem:       2028240    1824096     204144          0      70708     364180
-/+ buffers/cache:    1389208     639032
Swap:      3905532     157076    3748456

             total       used       free     shared    buffers     cached
Mem:       2028240    1824192     204048          0      70716     364212
-/+ buffers/cache:    1389264     638976
Swap:      3905532     157076    3748456
```
阅读更多10个Free命令使用实例
http://www.tecmint.com/10-examples-of-linux-free-command/	


# 57. mysqldump 命令

好了，现在你从名字上就能明白这个命令所代表的作用。mysqldump 命令会转储(备份)数据库的全部或特定一部分数据到一个给定的文件中。例如：

```
[avishek@tecmint ~]$ mysqldump -u root -p --all-databases > /home/server/Desktop/backupfile.sql
```
注意： mysqldump 需要 mysql 在运行中并且有正确的授权密码。我们在 用mysqldump命令备份数据库中讨论了一些有用的 “mysqldump” 命令用法。 
http://www.tecmint.com/mysql-backup-and-restore-commands-for-database-administration/


# 58. mkpasswd 命令

根据指定的长度，产生一个难猜的随机密码。

[avishek@tecmint ~]$ mkpasswd -l 10

zI4+Ybqfx9

[avishek@tecmint ~]$ mkpasswd -l 20 

w0Pr7aqKk&hmbmqdrlmk

注意： -l 10 产生一个10个字符的随机密码，而-l 20 产生 20个字符的密码,它可以设置为任意长度来取得所希望的结果。这个命令很有用，经常在脚本语言里使用来产生随机的密码。你可能需要 yum 或 apt ‘expect’ 包来使用这个命令。

```
[avishek@tecmint ~]$ yum install expect 
或
[avishek@tecmint ~]$ apt-get install expect
```

# 59. Command: paste

合并两个或多个文本文件，按行来进行合并。示例。如果 file1 的内容是：

1 
2 
3 

file2 是这样的: 

a 
b 
c 
d

```
[avishek@tecmint ~]$ paste file1 file2 > file3
```

结果file3将是: 
1    a 
2    b 
3    c 
     d



# 60.Command: lsof

lsof 是"list open files("列表中打开的文件") 的缩写，显示您的系统当前已打开的所有文件。这是非常有用的对于想找出哪些进程使用某一特定文件，或显示为单个进程打开所有文件。一些有用的 10 个lsof 命令示例，你可能会感兴趣阅读。

```
[avishek@tecmint ~]$ lsof 

COMMAND     PID   TID            USER   FD      TYPE     DEVICE SIZE/OFF       NODE NAME
init          1                  root  cwd       DIR        8,1     4096          2 /
init          1                  root  rtd       DIR        8,1     4096          2 /
```