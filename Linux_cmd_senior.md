http://www.oschina.net/translate/20-advanced-commands-for-middle-level-linux-users?lang=chs&page=2#

# 21. 命令: Find

搜索指定目录下的文件，从开始于父目录，然后搜索子目录。

```
root@tecmint:~# find -name *.sh 

./Desktop/load.sh 
./Desktop/test.sh 
./Desktop/shutdown.sh 
```
注意： `-name‘选项是搜索大小写敏感。可以使用`-iname‘选项，这样在搜索中可以忽略大小写。（*是通配符，可以搜索所有的文件；‘.sh‘你可以使用文件名或者文件名的一部分来制定输出结果）

```
root@tecmint:~# find -iname *.SH ( find -iname *.Sh /  find -iname *.sH)

./Desktop/load.sh 
./Desktop/test.sh 
./Desktop/shutdown.sh 
./Binary/firefox/run-mozilla.sh 
./Downloads/kdewebdev-3.5.8/quanta/scripts/externalpreview.sh 
./Downloads/kdewebdev-3.5.8/admin/doxygen.sh 
./Downloads/kdewebdev-3.5.8/admin/cvs.sh 
./Downloads/kdewebdev-3.5.8/admin/ltmain.sh 
./Downloads/wheezy-nv-install.sh
```
```
root@tecmint:~# find -name *.tar.gz 

/var/www/modules/update/tests/aaa_update_test.tar.gz 
./var/cache/flashplugin-nonfree/install_flash_player_11_linux.i386.tar.gz 
./home/server/Downloads/drupal-7.22.tar.gz 
```
注意：以上命令查找根目录下和所有文件夹以及加载的设备的子目录下的所有包含‘tar.gz'的文件。

’find'命令的更详细信息请参考35 Find Command Examples in Linux
http://www.tecmint.com/35-practical-examples-of-linux-find-command/


# 22. 命令: grep

‘grep‘命令搜索指定文件中包含给定字符串或者单词的行。举例搜索‘/etc/passwd‘文件中的‘tecmint'

```
root@tecmint:~# grep tecmint /etc/passwd 

tecmint:x:1000:1000:Tecmint,,,:/home/tecmint:/bin/bash
```
使用’-i'选项将忽略大小写。

```
root@tecmint:~# grep -i TECMINT /etc/passwd 

tecmint:x:1000:1000:Tecmint,,,:/home/tecmint:/bin/bash
```
使用’-r'选项递归搜索所有自目录下包含字符串 “127.0.0.1“.的行。

```
root@tecmint:~# grep -r "127.0.0.1" /etc/ 

/etc/vlc/lua/http/.hosts:127.0.0.1
/etc/speech-dispatcher/modules/ivona.conf:#IvonaServerHost "127.0.0.1"
/etc/mysql/my.cnf:bind-address		= 127.0.0.1
/etc/apache2/mods-available/status.conf:    Allow from 127.0.0.1 ::1
```
注意：您还可以使用以下选项：

- -w 搜索单词 (egrep -w ‘word1|word2‘ /path/to/file).
- -c 用于统计满足要求的行 (i.e., total number of times the pattern matched) (grep -c ‘word‘ /path/to/file).
- –color 彩色输出 (grep –color server /etc/passwd).



# 23. 命令: man

‘man‘是系统帮助页。Man提供命令所有选项及用法的在线文档。几乎所有的命令都有它们的帮助页，例如：

```
root@tecmint:~# man man

MAN(1)                                                               Manual pager utils                                                              MAN(1)

NAME
       man - an interface to the on-line reference manuals

SYNOPSIS
       man  [-C  file]  [-d]  [-D]  [--warnings[=warnings]] 
```
上面是man命令的系统帮助页，类似的有cat和ls的帮助页。
注意：系统帮助页是为了命令的使用和学习而设计的。 



# 24. 命令: ps

ps命令给出正在运行的某个进程的状态，每个进程有特定的id成为PID。

```
root@tecmint:~# ps

 PID TTY          TIME CMD
 4170 pts/1    00:00:00 bash
 9628 pts/1    00:00:00 ps
```
使用‘-A‘选项可以列出所有的进程及其PID。

```
root@tecmint:~# ps -A

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:01 ksoftirqd/0
    5 ?        00:00:00 kworker/0:0H
    7 ?        00:00:00 kworker/u:0H
    8 ?        00:00:00 migration/0
    9 ?        00:00:00 rcu_bh
....
```
注意：当你要知道有哪些进程在运行或者需要知道想杀死的进程PID时ps命令很管用。你可以把它与‘grep‘合用来查询指定的输出结果，例如：

```
root@tecmint:~# ps -A | grep -i ssh

 1500 ?        00:09:58 sshd
 4317 ?        00:00:00 sshd
```
ps命令与grep命令用管道线分割可以得到我们想要的结果。



# 25. 命令: kill

也许你从命令的名字已经猜出是做什么的了,kill是用来杀死已经无关紧要或者没有响应的进程.它是一个非常有用的命令,而不是非常非常有用.你可能很熟悉Windows下要杀死进程可能需要频繁重启机器因为一个在运行的进程大部分情况下不能够杀死,即使杀死了进程也需要重新启动操作系统才能生效.但在linux环境下,事情不是这样的.你可以杀死一个进程并且重启它而不是重启整个操作系统.

杀死一个进程需要知道进程的PID.

假设你想杀死已经没有响应的‘apache2'进程,运行如下命令:

```
root@tecmint:~# ps -A | grep -i apache2

1285 ?        00:00:00 apache2
```
搜索‘apache2'进程,找到PID并杀掉它.例如:在本例中‘apache2'进程的PID是1285..

```
root@tecmint:~# kill 1285 (to kill the process apache2)
```
注意:每次你重新运行一个进程或者启动系统,每个进程都会生成一个新的PID.你可以使用ps命令获得当前运行进程的PID.

另一个杀死进程的方法是:

```
root@tecmint:~# pkill apache2
```
注意:kill需要PID作为参数,pkill可以选择应用的方式,比如指定进程的所有者等.




# 26. 命令: whereis

whereis的作用是用来定位命令的二进制文件\资源\或者帮助页.举例来说,获得ls和kill命令的二进制文件/资源以及帮助页:

```
root@tecmint:~# whereis ls 

ls: /bin/ls /usr/share/man/man1/ls.1.gz

root@tecmint:~# whereis kill

kill: /bin/kill /usr/share/man/man2/kill.2.gz /usr/share/man/man1/kill.1.gz
```
注意:当需要知道二进制文件保存位置时有用.



# 27. 命令: service

‘service‘命令控制服务的启动、停止和重启，它让你能够不重启整个系统就可以让配置生效以开启、停止或者重启某个服务。

在Ubuntu上启动apache2 server：

```
root@tecmint:~# service apache2 start

 * Starting web server apache2                                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 1285) already running						[ OK ]
```
重启apache2 server：

```
root@tecmint:~# service apache2 restart

* Restarting web server apache2                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName  [ OK ]
```
停止apache2 server：

```
root@tecmint:~# service apache2 stop

 * Stopping web server apache2                                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting                                                           		[ OK ]
```
注意：要想使用service命令，进程的脚本必须放在‘/etc/init.d‘，并且路径必须在指定的位置。

如果要运行“service apache2 start”实际上实在执行“service /etc/init.d/apache2 start”.



# 28. 命令: alias

alias是一个系统自建的shell命令，允许你为名字比较长的或者经常使用的命令指定别名。

我经常用‘ls -l‘命令，它有五个字符（包括空格）。于是我为它创建了一个别名‘l'。

```
root@tecmint:~# alias l='ls -l'
```
试试它是否能用：

```
root@tecmint:~# l

total 36 
drwxr-xr-x 3 tecmint tecmint 4096 May 10 11:14 Binary 
drwxr-xr-x 3 tecmint tecmint 4096 May 21 11:21 Desktop 
```
去掉’l'别名，要使用unalias命令：

```
root@tecmint:~# unalias l
```
再试试：

```
root@tecmint:~# l

bash: l: command not found
```
开个玩笑，把一个重要命令的别名指定为另一个重要命令：

```
alias cd='ls -l' (set alias of ls -l to cd)
alias su='pwd' (set alias of pwd to su)
....
(You can create your own)
....
```
想想多么有趣，现在如果你的朋友敲入‘cd'命令，当他看到的是目录文件列表而不是改变目录；当他试图用’su‘命令时，他会进入当前目录。你可以随后去掉别名，向他解释以上情况。



# 29.命令: df

报告系统的磁盘使用情况。在跟踪磁盘使用情况方面对于普通用户和系统管理员都很有用。 ‘df‘ 通过检查目录大小工作，但这一数值仅当文件关闭时才得到更新。

```
root@tecmint:~# df

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       47929224 7811908  37675948  18% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1005916       4   1005912   1% /dev
tmpfs             202824     816    202008   1% /run
none                5120       0      5120   0% /run/lock
none             1014120     628   1013492   1% /run/shm
none              102400      44    102356   1% /run/user
/dev/sda5         184307   79852     94727  46% /boot
/dev/sda7       95989516   61104  91045676   1% /data
/dev/sda8       91953192   57032  87218528   1% /personal
```
‘df’命令的更多例子请参阅 12 df Command Examples in Linux.
http://www.tecmint.com/how-to-check-disk-space-in-linux/


# 30. 命令: du

估计文件的空间占用。 逐层统计文件（例如以递归方式）并输出摘要。

```
root@tecmint:~# du

8       ./Daily Pics/wp-polls/images/default_gradient
8       ./Daily Pics/wp-polls/images/default
32      ./Daily Pics/wp-polls/images
8       ./Daily Pics/wp-polls/tinymce/plugins/polls/langs
8       ./Daily Pics/wp-polls/tinymce/plugins/polls/img
```
注意: ‘df‘ 只显示文件系统的使用统计，但‘du‘统计目录内容。‘du‘命令的更详细信息请参阅10 du (Disk Usage) Commands.
http://www.tecmint.com/check-linux-disk-usage-of-files-and-directories/



# 31. 命令: rm

'rm' 标准移除命令。 rm 可以用来删除文件和目录。
删除目录

```
root@tecmint:~# rm PassportApplicationForm_Main_English_V1.0

rm: cannot remove `PassportApplicationForm_Main_English_V1.0': Is a directory
```
'rm' 不能直接删除目录,需要加上相应的'-rf'参数才可以。

```
root@tecmint:~# rm -rf PassportApplicationForm_Main_English_V1.0
```
警告: "rm -rf" 命令是一个破坏性的命令,假如你不小心删除一个错误的目录。一旦你使用'rm -rf' 删除一个目录,在目录中所有的文件包括目录本身会被永久的删除,所以使用这个命令要非常小心。



# 32. 命令: echo

echo  的功能正如其名，就是基于标准输出打印一段文本。它和shell无关，shell也不读取通过echo命令打印出的内容。然而在一种交互式脚本中，echo通过终端将信息传递给用户。它是在脚本语言，交互式脚本语言中经常用到的命令。

```
root@tecmint:~# echo "Tecmint.com is a very good website" 

Tecmint.com is a very good website
```

创建一小段交互式脚本

1. 在桌面上新建一个文件，命名为 ‘interactive_shell.sh‘  (记住必须带 ‘.sh‘扩展名)。
2. 复制粘贴如下脚本代码，确保和下面的一致。

```
#!/bin/bash 
echo "Please enter your name:" 
   read name 
   echo "Welcome to Linux $name"
```
接下来，设置执行权限并运行脚本。

```
root@tecmint:~# chmod 777 interactive_shell.sh

root@tecmint:~# ./interactive_shell.sh

Please enter your name:
Ravi Saive
Welcome to Linux Ravi Saive
```

注意: ‘#!/bin/bash‘ 告诉shell这是一个脚本，并且在脚本首行写上这句话是个好习惯。. ‘read‘ 读取给定的输出.



# 33. 命令: passwd

这是一个很重要的命令，在终端中用来改变自己密码很有用。显然的，因为安全的原因，你需要知道当前的密码。

```
root@tecmint:~# passwd 

Changing password for tecmint. 
(current) UNIX password: ******** 
Enter new UNIX password: ********
Retype new UNIX password: ********
Password unchanged   [这里表示密码未改变，例如：新密码=旧密码]
Enter new UNIX password: #####
Retype new UNIX password:#####
```


# 34. 命令: lpr

这个命令用来在命令行上将指定的文件在指定的打印机上打印。

```
root@tecmint:~# lpr -P deskjet-4620-series 1-final.pdf
```
注意： "lpq"命令让你查看打印机的状态（是开启状态还是关闭状态）和等待打印中的工作(文件)的状态。





# 35. 命令: cmp

比较两个任意类型的文件并将结果输出至标准输出。如果两个文件相同， ‘cmp‘默认返回0；如果不同，将显示不同的字节数和第一处不同的位置。

以下面两个文件为例：
file1.txt

```
root@tecmint:~# cat file1.txt

Hi My name is Tecmint
```
file2.txt

```
root@tecmint:~# cat file2.txt

Hi My name is tecmint [dot] com
```
比较一下这两个文件，看看命令的输出。

```
root@tecmint:~# cmp file1.txt file2.txt 

file1.txt file2.txt differ: byte 15, line 1
```


# 36. 命令: wget

Wget是用于非交互式（例如后台）下载文件的免费工具.支持HTTP, HTTPS, FTP协议和 HTTP 代理。
使用wget下载ffmpeg

```
root@tecmint:~# wget http://downloads.sourceforge.net/project/ffmpeg-php/ffmpeg-php/0.6.0/ffmpeg-php-0.6.0.tbz2

--2013-05-22 18:54:52--  http://downloads.sourceforge.net/project/ffmpeg-php/ffmpeg-php/0.6.0/ffmpeg-php-0.6.0.tbz2
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 216.34.181.59

100%[===========================================================================>] 2,75,557    67.8KB/s   in 4.0s   

2013-05-22 18:55:00 (67.8 KB/s) - ‘ffmpeg-php-0.6.0.tbz2’ saved [275557/275557]
```




# 37 命令: mount

mount 是一个很重要的命令，用来挂载不能自动挂载的文件系统。你需要root权限挂载设备。

在插入你的文件系统后，首先运行"lsblk"命令，识别出你的设备，然后把分配的设备名记下来。

```
root@tecmint:~# lsblk 

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT 
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0 923.6G  0 part / 
├─sda2   8:2    0     1K  0 part 
└─sda5   8:5    0   7.9G  0 part [SWAP] 
sr0     11:0    1  1024M  0 rom  
sdb      8:16   1   3.7G  0 disk 
└─sdb1   8:17   1   3.7G  0 part
```
从这个输出上来看，很明显我插入的是4GB的U盘，因而“sdb1”就是要挂载上来的文件系统。以root用户操作，然后切换到/dev目录，它是所有文件系统挂载的地方。

```
root@tecmint:~# su
Password:

root@tecmint:~# cd /dev
```
创建一个任何名字的目录，但是最好和引用相关。

```
root@tecmint:~# mkdir usb
```
现在将“sdb1”文件系统挂载到“usb”目录.

```
root@tecmint:~# mount /dev/sdb1 /dev/usb
```
现在你就可以从终端进入到/dev/usb或者通过X窗口系统从挂载目录访问文件。
是时候让程序猿见识见识Linux环境是多么丰富了！




# 38. 命令: gcc

gcc 是Linux环境下C语言的内建编译器。下面是一个简单的C程序，在桌面上保存为Hello.c （记住必须要有‘.c‘扩展名）。

```
#include <stdio.h>
int main()
{
  printf("Hello world\n");
  return 0;
}
```
编译

```
root@tecmint:~# gcc Hello.c
```
运行

```
root@tecmint:~# ./a.out 

Hello world
```
注意: 编译C程序时，输出会自动保存到一个名为“a.out”的新文件，因此每次编译C程序 “a.out”都会被修改。 因此编译期间最好定义输出文件名.，这样就不会有覆盖输出文件的风险了。
用这种方法编译

```
root@tecmint:~# gcc -o Hello Hello.c
```
这里‘-o‘将输出写到‘Hello‘文件而不是 ‘a.out‘。再运行一次。

```
root@tecmint:~# ./Hello 

Hello world
```



# 39. 命令: g++

g++是C++的内建编译器。下面是一个简单的C++程序，在桌面上保存为Add.cpp （记住必须要有‘.cpp‘扩展名）。

```
#include <iostream>

using namespace std;

int main() 
    {
          int a;
          int b;
          cout<<"Enter first number:\n";
          cin >> a;
          cout <<"Enter the second number:\n";
          cin>> b;
          cin.ignore();
          int result = a + b;
          cout<<"Result is"<<"  "<<result<<endl;
          cin.get();
          return 0;
     }
```
编译

```
root@tecmint:~# g++ Add.cpp
```
运行

```
root@tecmint:~# ./a.out

Enter first number: 
...
...
```
注意:编译C++程序时，输出会自动保存到一个名为“a.out”的新文件，因此每次编译C++程序 “a.out”都会被修改。 因此编译期间最好定义输出文件名.，这样就不会有覆盖输出文件的风险了。
用这种方法编译

```
root@tecmint:~# g++ -o Add Add.cpp
```
运行

```
root@tecmint:~# ./Add 

Enter first number: 
...
...
```




# 40. 命令: java

Java 是世界上使用最广泛的编程语言之一. 它也被认为是高效, 安全和可靠的编程语言. 现在大多数基于网络的服务都使用Java实现. 

拷贝以下代码到一个文件就可以创建一个简单的Java程序. 不妨把文件命名为tecmint.java (记住: '.java'扩展名是必需的).

```
class tecmint {
  public static void main(String[] arguments) {
    System.out.println("Tecmint ");
  }
}
```
用javac编译tecmint.java

```
root@tecmint:~# javac tecmint.java
```
运行

```
root@tecmint:~# java tecmint
```
注意: 几乎所有的Linux发行版都带有gcc编译器, 大多数发行版都内建了g++ 和 java 编译器, 有些也可能没有. 你可以用apt 或 yum 安装需要的包. 

