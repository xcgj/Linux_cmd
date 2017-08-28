http://www.oschina.net/translate/useful-linux-commands-for-newbies?lang=chs&page=2#

# 1. ls命令

ls命令是列出目录内容(List Directory Contents)的意思。运行它就是列出文件夹里的内容，可能是文件也可能是文件夹。

```
root@tecmint:~# ls

Android-Games                     Music
Pictures                          Public
Desktop                           Tecmint.com
Documents                         TecMint-Sync
Downloads                         Templates
```

## “ls -l”命令
以详情模式(long listing fashion)列出文件夹的内容。

```
root@tecmint:~# ls -l

total 40588
drwxrwxr-x 2 ravisaive ravisaive     4096 May  8 01:06 Android Games
drwxr-xr-x 2 ravisaive ravisaive     4096 May 15 10:50 Desktop
drwxr-xr-x 2 ravisaive ravisaive     4096 May 16 16:45 Documents
drwxr-xr-x 6 ravisaive ravisaive     4096 May 16 14:34 Downloads
drwxr-xr-x 2 ravisaive ravisaive     4096 Apr 30 20:50 Music
drwxr-xr-x 2 ravisaive ravisaive     4096 May  9 17:54 Pictures
drwxrwxr-x 5 ravisaive ravisaive     4096 May  3 18:44 Tecmint.com
drwxr-xr-x 2 ravisaive ravisaive     4096 Apr 30 20:50 Templates
```

## "ls -a"命令
会列出文件夹里的所有内容，包括以"."开头的隐藏文件。

```
root@tecmint:~# ls -a

.			.gnupg			.dbus			.goutputstream-PI5VVW		.mission-control
.adobe                  deja-dup                .grsync                 .mozilla                 	.themes
.gstreamer-0.10         .mtpaint                .thumbnails             .gtk-bookmarks          	.thunderbird
.HotShots               .mysql_history          .htaccess		.apport-ignore.xml      	.ICEauthority           
.profile                .bash_history           .icons                  .bash_logout                    .fbmessenger
.jedit                  .pulse                  .bashrc                 .liferea_1.8             	.pulse-cookie            
.Xauthority		.gconf                  .local                  .Xauthority.HGHVWW		.cache
.gftp                   .macromedia             .remmina                .cinnamon                       .gimp-2.8
.ssh                    .xsession-errors 	.compiz                 .gnome                          teamviewer_linux.deb          
.xsession-errors.old	.config                 .gnome2                 .zoncolor
```

注意：在Linux中，文件以“.”开头的就是隐藏文件，并且每个文件，文件夹，设备或者命令都是以文件对待。ls -l 命令输出：

- d (代表了是目录).
- rwxr-xr-x 是文件或者目录对所属用户，同一组用户和其它用户的权限。
- 上面例子中第一个ravisaive 代表了文件文件属于用户ravisaive
- 上面例子中的第二个ravisaive代表了文件文件属于用户组ravisaive
- 4096 代表了文件大小为4096字节.
- May 8 01:06 代表了文件最后一次修改的日期和时间.
- 最后面的就是文件/文件夹的名字


## "ls -lh"命令
With combination of -lh option, shows sizes in human readable format
结合了-lh选项，显示了人类可读格式的大小

```
# ls -lh
total 176K
-rw-r--r--. 1 root root  683 Aug 19 09:59 0001.pcap
-rw-------. 1 root root 1.6K Jul 31 02:17 anaconda-ks.cfg
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Desktop
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Documents
drwxr-xr-x. 4 root root 4.0K Aug 16 02:55 Downloads
-rw-r--r--. 1 root root  21K Aug 12 12:42 fbcmd_update.php
-rw-r--r--. 1 root root  46K Jul 31 09:58 index.html
-rw-r--r--. 1 root root  48K Jul 31 02:17 install.log
-rw-r--r--. 1 root root  12K Jul 31 02:13 install.log.syslog
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Music
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Pictures
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Public
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Templates
drwxr-xr-x. 2 root root 4.0K Jul 31 02:48 Videos
```

## "ls -F"
Using -F option with ls command, will add the ‘/’ Character at the end each directory.
使用ls命令使用-F选项，将在每个目录末尾添加/字符

```
# ls -F
0001.pcap        Desktop/    Downloads/        index.html   install.log.syslog  Pictures/  Templates/
anaconda-ks.cfg  Documents/  fbcmd_update.php  install.log  Music/              Public/    Videos/
```

## "ls -r"
The following command with ls -r option display files and directories in reverse order.
下面的命令使用ls-r选项显示文件和目录以相反的顺序显示

```
# ls -r
Videos     Public    Music               install.log  fbcmd_update.php  Documents  anaconda-ks.cfg
Templates  Pictures  install.log.syslog  index.html   Downloads         Desktop    0001.pcap

```

## "ls -R"
Recursively list Sub-Directories. ls -R option will list very long listing directory trees. See an example of output of the command.
递归地列出子目录, ls-R选项将列出非常长的列表目录树。请参见命令输出的示例

```
# ls -R
total 1384
-rw-------. 1 root     root      33408 Aug  8 17:25 anaconda.log
-rw-------. 1 root     root      30508 Aug  8 17:25 anaconda.program.log
./httpd:
total 132
-rw-r--r--  1 root root     0 Aug 19 03:14 access_log
-rw-r--r--. 1 root root 61916 Aug 10 17:55 access_log-20120812
./lighttpd:
total 68
-rw-r--r--  1 lighttpd lighttpd  7858 Aug 21 15:26 access.log
-rw-r--r--. 1 lighttpd lighttpd 37531 Aug 17 18:21 access.log-20120819
./nginx:
total 12
-rw-r--r--. 1 root root    0 Aug 12 03:17 access.log
-rw-r--r--. 1 root root  390 Aug 12 03:17 access.log-20120812.gz
```

## ls -ltr
With combination of -ltr will shows latest modification file or directory date as last
使用-ltr的组合将显示最新的修改文件或目录日期
 
```
# ls -ltr
total 176
-rw-r--r--. 1 root root 11439 Jul 31 02:13 install.log.syslog
-rw-r--r--. 1 root root 48867 Jul 31 02:17 install.log
-rw-------. 1 root root  1586 Jul 31 02:17 anaconda-ks.cfg
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Desktop
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Videos
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Templates
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Public
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Pictures
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Music
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Documents
```

## "ls -lS"
按文件大小排序文件, 结合-lS显示文件大小的顺序，首先显示大的尺寸

```
# ls -lS
total 176
-rw-r--r--. 1 root root 48867 Jul 31 02:17 install.log
-rw-r--r--. 1 root root 46701 Jul 31 09:58 index.html
-rw-r--r--. 1 root root 21262 Aug 12 12:42 fbcmd_update.php
-rw-r--r--. 1 root root 11439 Jul 31 02:13 install.log.syslog
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Desktop
drwxr-xr-x. 2 root root  4096 Jul 31 02:48 Documents
```

## "ls -i"
显示文件或目录的索引号(inode number), 在文件/目录名之前，我们可以看到一些数字。使用-i选项列表文件/目录，带有inode号

```
## "ls -i"
20112 0001.pcap        23610 Documents         23793 index.html          23611 Music     23597 Templates
23564 anaconda-ks.cfg  23595 Downloads            22 install.log         23612 Pictures  23613 Videos
23594 Desktop          23585 fbcmd_update.php     35 install.log.syslog  23601 Public
```

## "ls --version"
显示ls命令的版本

```
# ls --version
ls (GNU coreutils) 8.4
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Written by Richard M. Stallman and David MacKenzie.
```


## "ls --help"
列出ls命令的帮助页面

```
# ls --help
Usage: ls [OPTION]... [FILE]...
```

## "ls -l 路径"
列出指定目录下的信息

```
# ls -l /tmp
total 408
drwx------. 2 narad narad   4096 Aug  2 02:00 CRX_75DAF8CB7768
-r--------. 1 root  root  384683 Aug  4 12:28 htop-1.0.1.tar.gz
drwx------. 2 root  root    4096 Aug  4 11:20 keyring-6Mfjnk
drwx------. 2 root  root    4096 Aug 16 01:33 keyring-pioZJr
drwx------. 2 gdm   gdm     4096 Aug 21 11:26 orbit-gdm
```

## "ls -l 路径"
列出指定目录的信息

```
# ls -ld /tmp/
drwxrwxrwt. 13 root root 4096 Aug 21 12:48 /tmp/
```

## "ls -n"
显示文件和目录的UID和GID。使用选项-n和ls命令

```
# ls -n
total 36
drwxr-xr-x. 2 500 500 4096 Aug  2 01:52 Downloads
drwxr-xr-x. 2 500 500 4096 Aug  2 01:52 Music
drwxr-xr-x. 2 500 500 4096 Aug  2 01:52 Pictures
-rw-rw-r--. 1 500 500   12 Aug 21 13:06 tmp.txt
drwxr-xr-x. 2 500 500 4096 Aug  2 01:52 Videos
```

## ls命令和它的别名
为ls命令设置别名，当我们执行ls命令时，它将默认选择-l选项，并显示列表

```
# alias ls="ls -l"
```
注意:我们可以在您的系统中看到别名命令中可用的别名数，并且可以使用unalias删除前面定义的别名

```
# alias
alias cp='cp -i'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
```
```
# unalias ls
```

# 2. lsblk命令

"lsblk"就是列出块设备。除了RAM外，以标准的树状输出格式，整齐地显示块设备。

```
root@tecmint:~# lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
├─sda1   8:1    0  46.6G  0 part /
├─sda2   8:2    0     1K  0 part 
├─sda5   8:5    0   190M  0 part /boot
├─sda6   8:6    0   3.7G  0 part [SWAP]
├─sda7   8:7    0  93.1G  0 part /data
└─sda8   8:8    0  89.2G  0 part /personal
sr0     11:0    1  1024M  0 rom
```

## “lsblk -l”命令
以列表格式显示块设备(而不是树状格式)。

```
root@tecmint:~# lsblk -l

NAME MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda    8:0    0 232.9G  0 disk 
sda1   8:1    0  46.6G  0 part /
sda2   8:2    0     1K  0 part 
sda5   8:5    0   190M  0 part /boot
sda6   8:6    0   3.7G  0 part [SWAP]
sda7   8:7    0  93.1G  0 part /data
sda8   8:8    0  89.2G  0 part /personal
sr0   11:0    1  1024M  0 rom
```

注意：lsblk是最有用和最简单的方式来了解新插入的USB设备的名字，特别是当你在终端上处理磁盘/块设备时。


# 3. md5sum命令

“md5sum”就是计算和检验MD5信息签名。md5 checksum(通常叫做哈希)使用匹配或者验证文件的文件的完整性，因为文件可能因为传输错误，磁盘错误或者无恶意的干扰等原因而发生改变。

```
root@tecmint:~# md5sum teamviewer_linux.deb 

47790ed345a7b7970fc1f2ac50c97002  teamviewer_linux.deb
```

注意：用户可以使用官方提供的和md5sum生成签名信息匹对以此检测文件是否改变。Md5sum没有sha1sum安全，这点我们稍后讨论。



# 4. dd命令

“dd”命令代表了转换和复制文件。可以用来转换和复制文件，大多数时间是用来复制iso文件(或任何其它文件)到一个usb设备(或任何其它地方)中去，所以可以用来制作USB启动器。

```
root@tecmint:~# dd if=/home/user/Downloads/debian.iso of=/dev/sdb1 bs=512M; sync
```

注意：在上面的例子中，usb设备就是sdb1（你应该使用lsblk命令验证它，否则你会重写你的磁盘或者系统），请慎重使用磁盘的名，切忌。

dd 命令在执行中会根据文件的大小和类型 以及 usb设备的读写速度，消耗几秒到几分钟不等。



# 5. uname命令

"uname"命令就是Unix Name的简写。显示机器名，操作系统和内核的详细信息。

```
root@tecmint:~# uname -a

Linux tecmint 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686 i686 i686 GNU/Linux
```

注意： uname显示内核类别， uname -a显示详细信息。上面的输出详细说明了uname -a

- “Linux“: 机器的内核名
- “tecmint“: 机器的节点名
- “3.8.0-19-generic“: 内核发布版本
- “#30-Ubuntu SMP“: 内核版本
- “i686“: 处理器架构
- “GNU/Linux“: 操作系统名

# 6. history命令

“history”命令就是历史记录。它显示了在终端中所执行过的所有命令的历史。

```
root@tecmint:~# history

 1  sudo add-apt-repository ppa:tualatrix/ppa
 2  sudo apt-get update
 3  sudo apt-get install ubuntu-tweak
 4  sudo add-apt-repository ppa:diesch/testing
 5  sudo apt-get update
 6  sudo apt-get install indicator-privacy
 7  sudo add-apt-repository ppa:atareao/atareao
 8  sudo apt-get update
 9  sudo apt-get install my-weather-indicator
```

注意：按住“CTRL + R”就可以搜索已经执行过的命令，它可以在你写命令时自动补全。

```
(reverse-i-search)`if': ifconfig
```



# 7. sudo命令

“sudo”(super user do)命令允许授权用户执行超级用户或者其它用户的命令。通过在sudoers列表的安全策略来指定。

```
root@tecmint:~# sudo add-apt-repository ppa:tualatrix/ppa
```

注意：sudo 允许用户借用超级用户的权限，然而"su"命令实际上是允许用户以超级用户登录。所以sudo比su更安全。
并不建议使用sudo或者su来处理日常用途，因为它可能导致严重的错误如果你意外的做错了事，这就是为什么在linux社区流行一句话：

    “To err is human, but to really foul up everything, you need root password.” 

    “人非圣贤孰能无过，但是拥有root密码就真的万劫不复了。” # 译 



# 8. mkdir命令

“mkdir”(Make directory)命令在命名路径下创建新的目录。然而如果目录已经存在了，那么它就会返回一个错误信息"不能创建文件夹，文件夹已经存在了"("cannot create folder, folder already exists")

```
root@tecmint:~# mkdir tecmint
```

注意：目录只能在用户拥有写权限的目录下才能创建。mkdir：不能创建目录`tecmint`，因为文件已经存在了。（上面的输出中不要被文件迷惑了，你应该记住我开头所说的-在linux中，文件，文件夹，驱动，命令，脚本都视为文件）




# 9. touch 命令

“touch”命令代表了将文件的访问和修改时间更新为当前时间。touch命令只会在文件不存在的时候才会创建它。如果文件已经存在了，它会更新时间戳，但是并不会改变文件的内容。

```
root@tecmint:~# touch tecmintfile
```

注意：touch 可以用来在用户拥有写权限的目录下创建不存在的文件。



# 10. chmod 命令

“chmod”命令就是改变文件的模式位。chmod会根据要求的模式来改变每个所给的文件，文件夹，脚本等等的文件模式（权限）。

在文件(文件夹或者其它，为了简单起见，我们就使用文件)中存在3中类型的权限

```
Read (r)=4
Write(w)=2
Execute(x)=1
```
所以如果你想给文件只读权限，就设置为'4';只写权限，设置权限为'2';只执行权限，设置为1; 读写权限，就是4+2 = 6, 以此类推。

现在需要设置3种用户和用户组权限。第一个是拥有者，然后是用户所在的组，最后是其它用户。

```
rwxr-x--x   abc.sh
```
这里root的权限是 rwx（读写和执行权限），
所属用户组权限是 r-x (只有读和执行权限, 没有写权限)，
对于其它用户权限是 -x(只有只执行权限)

为了改变它的权限，为拥有者，用户所在组和其它用户提供读，写，执行权限。

```
root@tecmint:~# chmod 777 abc.sh
```
三种都只有读写权限

```
root@tecmint:~# chmod 666 abc.sh
```
拥有者用户有读写和执行权限，用户所在的组和其它用户只有可执行权限

```
root@tecmint:~# chmod 711 abc.sh
```
注意：对于系统管理员和用户来说，这个命令是最有用的命令之一了。在多用户环境或者服务器上，对于某个用户，如果设置了文件不可访问，那么这个命令就可以解决，如果设置了错误的权限，那么也就提供了为授权的访问。




# 11. chown命令

“chown”命令就是改变文件拥有者和所在用户组。每个文件都属于一个用户组和一个用户。在你的目录下，使用"ls -l",你就会看到像这样的东西。

```
root@tecmint:~# ls -l 

drwxr-xr-x 3 server root 4096 May 10 11:14 Binary 
drwxr-xr-x 2 server server 4096 May 13 09:42 Desktop
```
在这里，目录Binary属于用户"server",和用户组"root",而目录"Desktop"属于用户“server”和用户组"server"

“chown”命令用来改变文件的所有权，所以仅仅用来管理和提供文件的用户和用户组授权。

```
root@tecmint:~# chown server:server Binary

drwxr-xr-x 3 server server 4096 May 10 11:14 Binary 
drwxr-xr-x 2 server server 4096 May 13 09:42 Desktop
```
注意：“chown”所给的文件改变用户和组的所有权到新的拥有者或者已经存在的用户或者用户组。




# 12. apt命令
This article explains how quickly you can learn to install, remove, update and search software packages using apt-get and apt-cache commands from the command line. This article provides some useful commands that will help you to handle package management in Debian/Ubuntu based systems
本文解释了使用从命令行中使用apt-get和apt-cache命令来安装、删除、更新和搜索软件包的速度有多快。本文提供了一些有用的命令，可以帮助您处理基于debian/ubuntu的系统中的包管理。

Debian(一种自由操作系统)系列以“apt”命令为基础，“apt”代表了Advanced Package Tool。APT是一个为Debian系列系统（Ubuntu，Kubuntu等等）开发的高级包管理器，在Gnu/Linux系统上，它会为包自动地，智能地搜索，安装，升级以及解决依赖。

```
root@tecmint:~# apt-get install mplayer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
...
```

```
root@tecmint:~# apt-get update

Hit http://ppa.launchpad.net raring Release.gpg                                           
Hit http://ppa.launchpad.net raring Release.gpg
...
```                                           
注意：上面的命令会导致系统整体的改变，所以需要root密码（查看提示符为"#"，而不是“$”）.和yum命令相比，Apt更高级和智能。

见名知义，
- apt-cache用来搜索包中是否包含子包mplayer, 
- apt-get用来安装，升级所有的已安装的包到最新版。

The apt-get utility is a powerful and free package management command line program, that is used to work with Ubuntu’s APT (Advanced Packaging Tool) library to perform installation of new software packages, removing existing software packages, upgrading of existing software packages and even used to upgrading the entire operating system.
apt-get实用程序是一个强大的和免费的包管理命令行程序,用于使用Ubuntu年代APT(先进的包装工具)库来执行安装新软件,删除现有的软件包,升级现有的软件包,甚至用来升级整个操作系统

The apt-cache command line tool is used for searching apt software package cache. In simple words, this tool is used to search software packages, collects information of packages and also used to search for what available packages are ready for installation on Debian or Ubuntu based systems
apt-cache命令行工具用于搜索apt软件包缓存。简而言之，这个工具用于搜索软件包，收集软件包的信息，并用于寻找可用的软件包准备在Debian或Ubuntu系统上安装的软件包。

## apt-cache-5有用的基本命令
### 1. 如何列出所有可用的包?

要列出所有可用的包，请键入以下命令。

```
$ apt-cache pkgnames

esseract-ocr-epo
pipenightdreams
mumudvb
...
```
### 2. 如何查找软件包名称和软件描述?

在安装之前找到包的名称和它的描述，使用“search”标志。使用apt - cache的“search”将显示一个匹配的包列表，并有简短的描述。
假设您想要找到包' vsftpd '的描述，命令将是

```
$ apt-cache search vsftpd

vsftpd - lightweight, efficient FTP server written for security
ccze - A robust, modular log coloriser
ftpd - File Transfer Protocol (FTP) server
yasat - simple stupid audit tool
```
要查找并列出starting with“vsftpd”的所有软件包，您可以使用以下命令

```
$ apt-cache pkgnames vsftpd

vsttpd
```

### 3. 如何检查包信息?

For example, if you would like to check information of package along with it short description say (version number, check sums, size, installed size, category etc). Use ‘show‘ sub command as shown below.
例如，如果您想要检查包的信息和它的简短描述(版本号、校验和、大小、安装大小、类别等)。使用“show”子命令，如下所示。

```
$ apt-cache show netcat

Package: netcat
Priority: optional
Section: universe/net
...
```

### 4. 如何检查特定包的依赖关系?

Use the ‘showpkg‘ sub command to check the dependencies for particular software packages. whether those dependencies packages are installed or not. For example, use the ‘showpkg‘ command along with package-name.
使用“showpkg”子命令检查特定软件包的依赖性, 不管这些包有没有安装。例如，使用“showpkg”命令和包名称。

```
$ apt-cache showpkg vsftpd

Package: vsftpd
Versions: 
2.3.5-3ubuntu1 (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages)
...
```

### 5. How Do I Check statistics of Cache

The ‘stats‘ sub command will display overall statistics about the cache. For example, the following command will display Total package names is the number of packages have found in the cache.
“stats”子命令将显示关于缓存的总体统计信息。例如，下面的命令将显示总包名，这是在缓存中找到的包数。

```
$ apt-cache stats

Total package names: 51868 (1,037 k)
Total package structures: 51868 (2,490 k)
Normal packages: 39505
Pure virtual packages: 602
Single virtual packages: 3819
Mixed virtual packages: 1052
Missing: 6890
Total distinct versions: 43015 (2,753 k)
Total distinct descriptions: 81048 (1,945 k)
Total dependencies: 252299 (7,064 k)
...
```


## APT-GET – 20个有用的基本命令
### 6. 如何更新系统包

The ‘update‘ command is used to resynchronize the package index files from the their sources specified in /etc/apt/sources.list file. The update command fetched the packages from their locations and update the packages to newer version.
‘update‘命令用于从其在/ etc / apt/sources中指定的源重新同步包索引文件。文件列表。update命令从它们的位置提取了包，并将包更新为新版本。

```
$ sudo apt-get update

[sudo] password for tecmint: 
Ign http://security.ubuntu.com quantal-security InRelease                      
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]                 
...
```

### 7. 如何升级软件包

The ‘upgrade‘ command is used to upgrade all the currently installed software packages on the system. Under any circumstances currently installed packages are not removed or packages which are not already installed neither retrieved and installed to satisfy upgrade dependencies.
‘upgrade‘命令用于升级系统上目前安装的所有软件包。在任何情况下，当前安装的包都不会被删除或包，这些包既没有被安装，也没有安装，以满足升级依赖。

```
$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
```

However, if you want to upgrade, unconcerned of whether software packages will be added or removed to fulfill dependencies, use the ‘dist-upgrade‘ sub command.
但是，如果您想要升级，不考虑添加或删除软件包是否满足依赖项，请使用“dist - upgrade”子命令。

```
$ sudo apt-get dist-upgrade
```

### 8. 如何安装或升级特定的软件包?

The ‘install‘ sub command is tracked by one or more packages wish for installation or upgrading.
一个或多个希望安装或升级的包写在‘install‘子命令后面。

```
$ sudo apt-get install netcat

Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
```

### 9.如何安装多个包?

You can add more than one package name along with the command in order to install multiple packages at the same time. For example, the following command will install packages ‘nethogs‘ and ‘goaccess‘.
您可以添加多个包名和命令，以便同时安装多个包。例如，下面的命令将安装包“nethogs”和“goaccess”。

```
$ sudo apt-get install nethogs goaccess

Reading package lists... Done
Building dependency tree       
...
```

### 10. 如何使用通配符安装几个包

With the help of regular expression you can add several packages with one string. For example, we use * wildcard to install several packages that contains the ‘*name*‘ string, name would be ‘package-name’.
在正则表达式的帮助下，可以用一个字符串添加几个包。例如，我们使用*通配符来安装几个包含“* name *”字符串的包，名称将是“package - name”。

```
$ sudo apt-get install '*name*'
```

### 11. 如何在不升级的情况下安装软件包

Using sub ‘–no-upgrade‘ command will prevent already installed packages from upgrading.
使用‘–no-upgrade‘命令将防止已经安装的软件包升级。

```
$ sudo apt-get install packageName --no-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
```

### 12. 如何只升级特定的软件包

The ‘–only-upgrade‘ command do not install new packages but it only upgrade the already installed packages and disables new installation of packages.
‘–only-upgrade‘命令不会安装新包，但它只会升级已经安装好的包，并禁用新安装包。

```
$ sudo apt-get install packageName --only-upgrade

Reading package lists... Done
Building dependency tree       
...
```

### 13. 如何安装特定的软件包版本?

Let’s say you wish to install only specific version of packages, simply use the ‘=‘ with the package-name and append desired version.
假设您希望仅安装包的特定版本，只需使用“=”连接包名和版本号。

```
$ sudo apt-get install vsftpd=2.3.5-3ubuntu1

Reading package lists... Done
Building dependency tree       
...
```

### 14. 如何删除包，但保留配置

To un-install software packages without removing their configuration files (for later re-use the same configuration). Use the ‘remove‘ command as shown.
在不删除配置文件的情况下卸载软件包(稍后再使用相同的配置)。如所示，使用‘remove‘命令。

```
$ sudo apt-get remove vsftpd

[sudo] password for tecmint: 
Reading package lists... Done
Building dependency tree       
...
```

### 15. 如何完全删除包

To remove software packages including their configuration files, use the ‘purge‘ sub command as shown below.
要删除包括其配置文件在内的软件包，请使用下面所示的‘purge‘子命令。

```
$ sudo apt-get purge vsftpd

Reading package lists... Done
Building dependency tree       
...
```
Alternatively, you can combine both the commands together as shown below.
或者，您可以将两个命令组合在一起，如下所示。

```
$ sudo apt-get remove --purge vsftpd

Reading package lists... Done
Building dependency tree       
...
```

### 16. 如何清理磁盘空间

The ‘clean‘ command is used to free up the disk space by cleaning retrieved (downloaded) .deb files (packages) from the local repository.
“clean”命令通过清理检索(下载)来释放磁盘空间。deb文件(包)来自本地存储库。

```
$ sudo apt-get clean
```

### 17. 我如何只下载包的源代码

To download only source code of particular package, use the option ‘–download-only source‘ with ‘package-name’ as shown.
若要下载特定软件包的源代码，请使用‘–download-only source‘+“包名”选项，如

```
$ sudo apt-get --download-only source vsftpd

Reading package lists... Done
Building dependency tree       
...
```

### 18. 我如何下载和解包一个包

To download and unpack source code of a package to a specific directory, type the following command.
要下载和解压包的源代码，请输入以下命令。

```
$ sudo apt-get source vsftpd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
```

### 19. 我如何下载、解包和编译一个包

You can also download, unpack and compile the source code at the same time, using option ‘–compile‘ as shown below.
您还可以同时下载、解压和编译源代码，使用选项“- compile”，如下所示。

```
$ sudo apt-get --compile source goaccess

[sudo] password for tecmint: 
Reading package lists... Done
...
```

### 20. 我如何在不安装的情况下下载软件包

Using ‘download‘ option, you can download any given package without installing it. For example, the following command will only download ‘nethogs‘ package to current working directory.
使用“下载”选项，您可以下载任何给定的包而不安装它。例如，下面的命令只将“nethogs”包下载到当前工作目录。

```
$ sudo apt-get download nethogs

Get:1 Downloading nethogs 0.8.0-1 [27.1 kB]
Fetched 27.1 kB in 3s (7,506 B/s)
```

### 21. 如何检查包的更改日志?

The ‘changelog‘ flag downloads a package change-log and shows the package version that is installed.
“changelog”标志下载一个包变更日志，并显示安装的包版本。

```
$ sudo apt-get changelog vsftpd

vsftpd (2.3.5-3ubuntu1) quantal; urgency=low
* Merge from Debian testing (LP: #1003644).  Remaining changes:
...
```

### 22. 如何检查已损坏的依赖项?

The ‘check‘ command is a diagnostic tool. It used to update package cache and checks for broken dependencies.
‘check‘命令是一种诊断工具。它用于更新包缓存和检查已损坏的依赖项。

```
$ sudo apt-get check

[sudo] password for tecmint: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

### 23. 如何搜索和构建依赖项?

This ‘build-dep‘ command searches the local repositories in the system and install the build dependencies for package. If the package does not exists in the local repository it will return an error code.
这个“build - dep”命令在系统中搜索本地存储库，并为包安装构建依赖项。如果包在本地存储库中不存在，它将返回一个错误代码。

```
$ sudo apt-get build-dep netcat

The following NEW packages will be installed:
debhelper dh-apparmor html2text po-debconf quilt
0 upgraded, 5 newly installed, 0 to remove and 328 not upgraded.
...
```

### 24. 如何自动清除apt - get缓存?

The ‘autoclean‘ command deletes all .deb files from /var/cache/apt/archives to free-up significant volume of disk space.
‘autoclean‘命令删除。deb文件从/ var/cache/apt/归档来增加大量磁盘空间。

```
$ sudo apt-get autoclean

Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

### 25. 如何自动删除已安装的软件包?

The ‘autoremove‘ sub command is used to auto remove packages that were certainly installed to satisfy dependencies for other packages and but they were now no longer required. For example, the following command will remove an installed package with its dependencies.
“autoremove”子命令用于自动删除已安装的包，以满足对其他包的依赖，但现在不再需要它们了。例如，以下命令将删除已安装的包及其依赖项。

```
$ sudo apt-get autoremove vsftpd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'vsftpd' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 328 not upgraded.
```

I’ve covered most of the available options with apt-get and apt-cache commands, but still there are more options available, you can check them out using ‘man apt-get‘ or ‘man apt-cache‘ from the terminal. 
我已经用apt-get和apt-cache命令覆盖了大部分可用选项，但仍然有更多可用的选项，您可以使用“man apt-get”或“man apt-cache”来检查它们。

Read Also : 20 用于包管理的有用的Linux YUM命令
https://www.tecmint.com/20-linux-yum-yellowdog-updater-modified-commands-for-package-mangement/


# 13. tar命令

“tar”命令是磁带归档(Tape Archive)，对创建一些文件的的归档和它们的解压很有用。

```
root@tecmint:~# tar -zxvf abc.tar.gz (记住'z'代表了.tar.gz)
```
```
root@tecmint:~# tar -jxvf abc.tar.bz2 (记住'j'代表了.tar.bz2)
```
```
root@tecmint:~# tar -cvf archieve.tar.gz(.bz2) /path/to/folder/abc
```
注意： "tar.gz"代表了使用gzip归档，“bar.bz2”使用bzip压缩的，它压缩的更好但是也更慢。

==========================
https://www.tecmint.com/18-tar-command-examples-in-linux/



# 14. cal 命令

“cal”（Calender），它用来显示当前月份或者未来或者过去任何年份中的月份。

```
root@tecmint:~# cal 

May 2013        
Su Mo Tu We Th Fr Sa  
          1  2  3  4  
 5  6  7  8  9 10 11  
12 13 14 15 16 17 18  
19 20 21 22 23 24 25  
26 27 28 29 30 31
```
显示已经过去的月份，1835年2月

```
root@tecmint:~# cal 02 1835

   February 1835      
Su Mo Tu We Th Fr Sa  
 1  2  3  4  5  6  7  
 8  9 10 11 12 13 14  
15 16 17 18 19 20 21  
22 23 24 25 26 27 28
```
显示未来的月份，2145年7月。

```
root@tecmint:~# cal 07 2145

     July 2145        
Su Mo Tu We Th Fr Sa  
             1  2  3  
 4  5  6  7  8  9 10  
11 12 13 14 15 16 17  
18 19 20 21 22 23 24  
25 26 27 28 29 30 31
```
注意： 你不需要往回调整日历50年，既不用复杂的数据计算你出生那天，也不用计算你的生日在哪天到来，[因为它的最小单位是月，而不是日]。




# 15. date命令

“date”命令使用标准的输出打印当前的日期和时间，也可以深入设置。

```
root@tecmint:~# date

Fri May 17 14:13:29 IST 2013

root@tecmint:~# date --set='14 may 2013 13:57' 

Mon May 13 13:57:00 IST 2013
```
注意：这个命令在脚本中十分有用，以及基于时间和日期的脚本更完美。而且在终端中改变日期和时间，让你更专业！！！（当然你需要root权限才能操作这个，因为它是系统整体改变）




# 16. cat命令

“cat”代表了连结（Concatenation），连接两个或者更多文本文件或者以标准输出形式打印文件的内容。

```
root@tecmint:~# cat a.txt b.txt c.txt d.txt abcd.txt

root@tecmint:~# cat abcd.txt
....
contents of file abcd
...
```
注意：“>>”和“>”调用了追加符号。它们用来追加到文件里，而不是显示在标准输出上。“>”符号会删除已存在的文件，然后创建一个新的文件。所以因为安全的原因，建议使用“>>”，它会写入到文件中，而不是覆盖或者删除。

## 通配符

在深入探究之前，我必须让你知道通配符(你应该知道通配符，它出现在大多数电视选秀中)。通配符是shell的特色，和任何GUI文件管理器相比，它使命令行更强大有力！如你所看到那样，在一个图形文件管理器中，你想选择一大组文件，你通常不得不使用你的鼠标来选择它们。这可能觉得很简单，但是事实上，这种情形很让人沮丧！

例如，假如你有一个有很多很多各种类型的文件和子目录的目录，然后你决定移动所有文件名中包含“Linux”字样的HTML文件到另外一个目录。如何简单的完成这个？如果目录中包含了大量的不同名的HTML文件，你的任务很巨大，而不是简单了。

在LInux CLI中，这个任务就很简单，就好像只移动一个HTML文件，因为有shell的通配符，才会如此简单。这些是特殊的字符，允许你选择匹配某种字符模式的文件名。它帮助你来选择，即使是大量文件名中只有几个字符，而且在大多数情形中，它比使用鼠标选择文件更简单。

这里就是常用通配符列表：

```
Wildcard Matches
   *			零个或者更多字符
   ?			恰好一个字符
[abcde]		        恰好列举中的一个字符
 [a-e]			恰好在所给范围中的一个字符
[!abcde]		任何字符都不在列举中 
[!a-e]			任何字符都不在所给的范围中
{debian,linux}		恰好在所给选项中的一整个单词
```
! 叫做非，带'！'的反向字符串为真

更多请阅读Linux cat 命令的实例 13 Linux中cat命令实例
http://www.tecmint.com/13-basic-cat-command-examples-in-linux/

## 1. Display Contents of File

In the below example, it will show contents of /etc/passwd file.

```
# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
narad:x:500:500::/home/narad:/bin/bash
```
## 2. View Contents of Multiple Files in terminal

In below example, it will display contents of test and test1 file in terminal.

```
# cat test test1
Hello everybody
Hi world,
```


## 3. Create a File with Cat Command

We will create a file called test2 file with below command.

```
# cat >test2
```
Awaits input from user, type desired text and press CTRL+D (hold down Ctrl Key and type ‘d‘) to exit. The text will be written in test2 file. You can see content of file with following cat command.

```
# cat test2
hello everyone, how do you do?
```

## 4. Use Cat Command with More & Less Options

If file having large number of content that won’t fit in output terminal and screen scrolls up very fast, we can use parameters more and less with cat command as show above.

```
# cat song.txt | more
# cat song.txt | less
```

## 5. Display Line Numbers in File

With -n option you could see the line numbers of a file song.txt in the output terminal.

```
# cat -n song.txt
1  "Heal The World"
2  There's A Place In
3  Your Heart
4  And I Know That It Is Love
5  And This Place Could
6  Be Much
7  Brighter Than Tomorrow
8  And If You Really Try
9  You'll Find There's No Need
10  To Cry
11  In This Place You'll Feel
12  There's No Hurt Or Sorrow
```


## 6. Display $ at the End of File

In the below, you can see with -e option that ‘$‘ is shows at the end of line and also in space showing ‘$‘ if there is any gap between paragraphs. This options is useful to squeeze multiple lines in a single line.

```
# cat -e test
hello everyone, how do you do?$
$
Hey, am fine.$
How's your training going on?$
$
```


## 7. Display Tab separated Lines in File

In the below output, we could see TAB space is filled up with ‘^I‘ character.

```
# cat -T test
hello ^Ieveryone, how do you do?
Hey, ^Iam fine.
^I^IHow's your training ^Igoing on?
Let's do ^Isome practice in Linux.
```

## 8. Display Multiple Files at Once

In the below example we have three files test, test1 and test2 and able to view the contents of those file as shown above. We need to separate each file with ; (semi colon).

```
# cat test; cat test1; cat test2
This is test file
This is test1 file.
This is test2 file.
```

## 9. Use Standard Output with Redirection Operator

We can redirect standard output of a file into a new file else existing file with ‘>‘ (greater than) symbol. Careful, existing contents of test1 will be overwritten by contents of test file.

```
# cat test > test1
```

## 10. Appending Standard Output with Redirection Operator

Appends in existing file with ‘>>‘ (double greater than) symbol. Here, contents of test file will be appended at the end of test1 file.

```
# cat test >> test1
```

## 11. Redirecting Standard Input with Redirection Operator

When you use the redirect with standard input ‘<‘ (less than symbol), it use file name test2 as a input for a command and output will be shown in a terminal.

```
# cat < test2
This is test2 file.
```

## 12. Redirecting Multiple Files Contain in a Single File

This will create a file called test3 and all output will be redirected in a newly created file.

```
# cat test test1 test2 > test3
```

## 13. Sorting Contents of Multiple Files in a Single File

This will create a file test4 and output of cat command is piped to sort and result will be redirected in a newly created file.
这将创建一个文件test4，并输出cat命令的输出，以进行排序，结果将在新创建的文件中重定向

```
# cat test test1 test2 test3 | sort > test4
```

# 17. cp 命令

“copy”就是复制。它会从一个地方复制一个文件到另外一个地方。

```
root@tecmint:~# cp /home/user/Downloads abc.tar.gz /home/user/Desktop (Return 0 when sucess)
```
注意： cp，在shell脚本中是最常用的一个命令，而且它可以使用通配符（在前面一块中有所描述），来定制所需的文件的复制。




# 18. mv 命令

“mv”命令将一个地方的文件移动到另外一个地方去。

```
root@tecmint:~# mv /home/user/Downloads abc.tar.gz /home/user/Desktop (Return 0 when sucess)
```
注意：mv 命令可以使用通配符。mv需谨慎使用，因为移动系统的或者未授权的文件不但会导致安全性问题，而且可能系统崩溃。



# 19. pwd 命令

```
“pwd”（print working directory），在终端中显示当前工作目录的全路径。

root@tecmint:~# pwd 

/home/user/Desktop
```
注意： 这个命令并不会在脚本中经常使用，但是对于新手，当从连接到nux很久后在终端中迷失了路径，这绝对是救命稻草。




# 20. cd 命令

最后，经常使用的“cd”命令代表了改变目录。它在终端中改变工作目录来执行，复制，移动，读，写等等操作。

```
root@tecmint:~# cd /home/user/Desktop

server@localhost:~$ pwd

/home/user/Desktop
```
注意： 在终端中切换目录时，cd就大显身手了。“cd ～”会改变工作目录为用户的家目录，而且当用户发现自己在终端中迷失了路径时，非常有用。“cd ..”从当前工作目录切换到(当前工作目录的)父目录。 