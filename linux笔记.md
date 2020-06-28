[TOC]

# 常识捷键记录

| 组合键位         | 功能说明                   |
| ---------------- | -------------------------- |
| `ctrl+alt+F1~F6` | 切换终端的显示             |
| `startx`         | 启动x11                    |
| `ctrl+u`         | 删除当前输入的所有bash文本 |
| `ctrl+a`         | 光标跳转到bash的首位       |
| `ctrl+e`         | 光标跳转到bash的末尾       |

# FHS目录协议

# 指令

## 

|      |                                                     |                    |
| :--- | --------------------------------------------------- | :----------------- |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      |                                                     |                    |
|      | `systemctl list-unit-files`  `systemctl list-units` | `chkconfig --list` |

## 系统信息的查看

| 需求说明                                    | 推荐指令选项                                             |
| ------------------------------------------- | -------------------------------------------------------- |
| 查看当前操作系统的版本                      | `uname -a`  `lsb_release -a`  `cat /proc/version`        |
| 输出PCI总线的简略信息                       | `lspci`                                                  |
| 输出PCI总线的详细信息                       | `lspci -v`                                               |
| 查看可读的系统开机的详细信息                | `dmesg-H`  `cat /var/log/dmesg`                          |
| 查看cpu的详细信息                           | `cat /proc/cpuinfo`                                      |
| 查看当前的内存状态信息                      | `free -h`  `cat /proc/meminfo`                           |
| 输出当前主机的文件系统信息fs                | `cat /proc/filesystems`                                  |
| 查看所有的挂载分区信息(树形或列表或键值对)  | `lsblk`  `lsblk -l`  `lsblk -P`  `fdisk -l`  `parted -l` |
| 查看所有挂载分区的文件系统***FS***          | `lsblk -f`                                               |
| 输出所有挂载分区的权限信息***permissions*** | `lsblk -m`                                               |
| 输出所有分区的拓扑结构                      | `lsblk -t`                                               |
| 输出当前主机的日期和时间                    | `date`                                                   |
| 查看当前主机的登陆用户信息                  | `who -a`  `w`                                            |
| 查看当前主机的用户的登陆历史                | `last`  可参考文件/var/log/wtmp                          |
| 输出当前主机的上线时间                      | `uptime`  可参考文件/var/run/utmp和/proc/uptime          |
| 间隔2秒统计5次,查看当前主机的内存状态信息   | `vmstat 2 5`                                             |
| 查看当前主机的所有磁盘数据                  | `vmstat -d`                                              |
| 查看当前主机指定的分区的硬盘数据            | `vmstat -p /dev/sda1`                                    |

## 系统资源的监视

| 需求说明                       | 推荐指令选项       |
| ------------------------------ | ------------------ |
| 打开类似windows的资源管理器    | `top`              |
| 查看当前主机中的所有进程的信息 | `ps -ef`  `ps aux` |
|                                |                    |
|                                |                    |
|                                |                    |

## 磁盘和分区的管理

| 需求说明                           | 推荐指令的选项          |
| ---------------------------------- | ----------------------- |
| 设定开机挂载指定磁盘分区的配置文件 | `/etc/fstab`            |
| 查看硬盘的分区信息                 | `fdisk -l`  `parted -l` |
| 查看分区的使用状况                 | `df -hiT`               |
| 查看etc文件夹占用空间的大小        | `du -sh /etc`           |
|                                    | `du -hd 1 /`            |
| 要了解的指令                       | `fsck`  `eject`         |
| 挂载和卸载分区的指令               | `mount`  `umount`       |

## 网络的管理

| 需求说明                                 | 推荐指令的选项                                               |
| ---------------------------------------- | ------------------------------------------------------------ |
| `配置文件`                               |                                                              |
| 网卡的配置文件                           | `/etc/sysconfig/network-scripts/ifcfg-ens33`                 |
| 回环地址的配置文件                       | `/etc/sysconfig/network-scripts/ifcfg-lo`                    |
| 主机名和网关的配置文件                   | `/etc/sysconfig/network`                                     |
| dns主机的配置文件                        | `/etc/resolv.conf`                                           |
| 主机和ip地址绑定的配置文件               | `/etc/hosts`                                                 |
| `相关的指令`                             |                                                              |
| 查看网卡的uuid信息                       | `nmcli con show` (centos7)  `nmcli con list`  (centos6)      |
| 查看网卡的mac地址                        | `nmcli dev show`  (centos7)  `nmcli dev list`  (centos6)     |
| 查看所有网卡的配置信息                   | `ifconfig`  `ip addr show`                                   |
| 启动ens33网卡                            | `ifup ens33`  `ifconfig ens33 up(不推荐)`  `ip link set dev ens33 up(不推荐)` |
| 卸载ens33网卡                            | `ifdown ens33`  `ifconfig ens33 down(不推荐)`  `ip link set dev ens down(不推荐)` |
| 使用ifconfig添加一个临时的ip别名         | `ifconfig ens33:0 add 192.168.1.131 netmask 255.255.255.0 up` |
| 使用ifconfig卸载添加的ip别名             | `ifconfig ens33:0 del 192.168.1.131`                         |
| 使用ip添加一个临时的ip别名               | `ip addr add 192.168.1.131/24 dev + brd dev ens33 label ens33:0` |
| 使用ip卸载添加的ip别名                   | `ip addr del 192.168.1.131/24 dev + brd dev ens33 label ens33:0` |
| 两台linux主机之间的文件传输指令          | `scp`                                                        |
| 以数字的形式监听主机的所有tcp和udp的端口 | `netstat -natup`                                             |
| 查看本地主机的路由表                     | `route -n`  `netstat -rn`                                    |
| 路由跟踪                                 | `traceroute`                                                 |
| 端口测试                                 | `telnet`                                                     |
| url地址下载                              | `wget`                                                       |
|                                          |                                                              |

## 用户的管理

| 需求说明           | 推荐指令选项      |
| ------------------ | ----------------- |
| `相关的配置文件`   |                   |
|                    | `/etc/passwd`     |
|                    | `/etc/shadow`     |
|                    | `/etc/group`      |
|                    |                   |
|                    |                   |
|                    |                   |
|                    | `/etc/sudoers`    |
| `相关的指令`       |                   |
| 切换指定的用户     | `su username`     |
| 切换到root用户     | `su -`            |
| 更改指定用户的密码 | `passwd username` |
| 更改root用户的密码 | `passwd`          |

## 文件的管理

| 需求说明                                     | 推荐指令选项                                  |
| -------------------------------------------- | --------------------------------------------- |
| 输出(指定目录)的(所有)文件                   | `ls`  `ls -al`  `ls -dl`  `ls -al /`          |
| 切换目录的工具                               | `cd`                                          |
| 查看当前位置的目录路径                       | `pwd`                                         |
| 创建单层目录                                 | `mkdir dirname`                               |
| 创建多层目录                                 | `mkdir -p dirname1/dirname2`                  |
| 创建一个文本文件或者修改文件的时间属性的工具 | `touch`                                       |
| 复制指定的文件                               | `cp filename filename.cp`                     |
| 复制指定的目录或者多层目录下的文件           | `cp -r dir1/dir2`  `cp -r dir1/dir2/filename` |
| 删除文件或者目录                             | `rm -rf`                                      |
| 移动文件或目录或者更改文件或目录的名称       | `mv`                                          |
| 创建一个硬链接                               | `ln 源文件位置 硬链接位置`                    |
| 创建一个符号链接                             | `ln -s 源文件位置 符号链接位置`               |
| 查看指定文件的文件类型的工具                 | `file`                                        |

## 文本的操作

| 需求说明       | 推荐指令的选项                               |
| -------------- | -------------------------------------------- |
| 文本查看的工具 | `cat`  `tac`  `less`  `more`  `head`  `tail` |
| 文本比较的工具 | `diff`                                       |
| 文本分割的工具 | `split`                                      |
| 文本查询的工具 | `find`                                       |
| 文本过滤的工具 | `grep`                                       |
|                |                                              |

## 备份和打包

传统的打包方式有zip;gz;bz2;tar.gz;tar.bz2这5种方式,当然不仅是局限于这几种.

| 需求说明                                           | 推荐指令的选项                                               |
| -------------------------------------------------- | ------------------------------------------------------------ |
| 递归的方式将指定的目录打包成zip的压缩包            | `zip -r 要打包的目录 打包后的zip文件`                        |
| 输出zip文件的压缩信息,但是不解压                   | `unzip -v zip文件`                                           |
| 解压zip文件到指定的目录下                          | `unzip zip文件 -d 要解压到的目录`                            |
| gz格式的压缩包,只针对文件,不能压缩目录.(仅作了解)  | gzip指令和gunzip指令                                         |
| bz2格式的压缩包,只针对文件,不能压缩目录.(仅作了解) | bzip2指令和bunzip2指令                                       |
| 将tar.gz压缩包解压到指定的目录                     | `tar -zxvf 压缩包 -C 要解压的目录`                           |
| 将指定的目录压缩为tar.gz文件                       | `tar -zcvf 压缩包 要压缩的目录`                              |
| 将tar.bz2压缩包解压到指定的目录                    | `tar -jxvf 压缩包 -C 要解压的目录`                           |
| 将指定的目录压缩为tar.bz2文件                      | `tar -jcvf 压缩包 要压缩的目录`                              |
| 使用dd将指定的目录或文件,打包到指定的文件          | `dd if=输入的文件 of=输出的文件`                             |
| 查询匹配的文件,使用cpio进行备份                    | `find /etc | cpio -ocvB > etc.bak.cpio`(恢复的时候按照备份时的路径策略) |
| 将cpio的备份文件进行恢复                           | `cpio -icduv < etc.bak.cpio`                                 |

## 软件包的管理

### rpm和srpm的区别

### 4种软件包的安装方式

源码编译的方式安装软件(apache2.2.4)

1. `rz`上传源码包
2. `tar -zxvf httpd-2.2.4.tar.gz >> tar.log`
3. `mkdir httpd`
4. `cd httpd-2.2.4`
5. `./configure --prefix=/home/admin/httpd >> /home/admin/configure.log`
6. `make >> /home/admin/make.log`
7. `make install >> /home/admin/make-install.log`
8. `cd ..`
9. `cd httpd/bin`
10. `sudo ./apachectl start`

> 报错:`httpd: Could not reliably determine the server's fully qualified domain name, using localhost.localdomain for ServerName`
>
> **解决方式** : 更改`httpd.cnf`配置文件,添加`ServerName localhost:80`
>
> 报错:`You don't have permission to access / on this server.`
>
> **解决方式** : 第一步,更改`httpd.cnf`配置文件,将`deny from all`更改为`allow from all`;再把`DocumentRoot`的值更改为`/var/www/html`.
>
> ​					第二步,执行`sudo mkdir /var/www; cd httpd; mv htdocs html; sudo mv html /var/www;`
>
> ​					第三步,执行`sudo apachectl restart`

二进制包的方式安装软件(maven为例)

1. `rz`上传二进制包
2. `tar -zxvf apache-maven-3.6.3-bin.tar.gz >> tar.log`
3. 配置环境变量`PATH`或者是切换到该包的`bin`目录中
4. 执行`mvn -version`验证即可

rpm的方式安装软件(apache2.4.6)

1. [登陆pkgs.org网站](https://pkgs.org/) 找到当前OS版本对应的rpm包的下载地址,执行`wget http://mirror.centos.org/centos/7/os/x86_64/Packages/httpd-2.4.6-93.el7.centos.x86_64.rpm`

   当然也可以使用yum指令安装,执行`yum install httpd --downloadonly --downloaddir=/home/admin/rpms`(推荐使用这种方式安装rpm包)

1. 执行`sudo rpm -ivh httpd-2.4.6-93.el7.centos.x86_64.rpm ` (注意!事先要把依赖的其他rpm包给安装)

1. 执行`sudo apachectl restart`或者`sudo service httpd start`

yum的方式安装软件(lrzsz为例)

1. `yum search lrzsz`
2. `yum install -y lrzsz`

### rpm指令常用选项

| 需求说明                           | 推荐指令选项                                                 |
| ---------------------------------- | ------------------------------------------------------------ |
| 安装指定的rpm包                    | `rpm -ivh lrzsz-0.12.20-36.el7.x86_64.rpm`(v表示输出附件信息,h表示输出hash标记#符号) |
| 不检查依赖关系,强制安装指定的rpm包 | `rpm -ivh lrzsz-0.12.20-36.el7.x86_64.rpm --nodeps`          |
| 查询本地是否存在具体的rpm包        | `rpm -q lrzsz-0.12.20-36.el7.x86_64.rpm`                     |
| 根据指令文件查询指令所属的安装包   | `rpm -qf /usr/bin/ls`                                        |
| 查询指定软件的所有安装文件         | `rpm -ql gcc`                                                |
| 查询指定软件的说明文件列表         | `rpm -qd net-tools`                                          |
| 查询指定软件的安装信息             | `rpm -qi gcc`                                                |
| 查询指定分组已安装的所有软件       | `rpm -qg 'Development/Languages'`                            |
| 验证具体软件包的状态               | `rpm -Vp lrzsz-0.12.20-36.el7.x86_64.rpm`                    |
| 验证具体软件包的文件               | `rpm -Vf lrzsz-0.12.20-36.el7.x86_64.rpm`                    |
| 验证具体软件包的GPG签名            | `rpm -K lrzsz-0.12.20-36.el7.x86_64.rpm`                     |
| 更新具体的软件包                   | `rpm -Uvh lrzsz-0.12.20-36.el7.x86_64.rpm`                   |
| 删除具体的软件包                   | `rpm -e lrzsz-0.12.20-36.el7.x86_64.rpm`                     |

### yum指令常用选项

yum 全称为 Yellow dog Updater, Modified ,是软件包管理器.

| 需求说明                                             | 推荐指令选项                                                 |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| 软件管理工具yum的配置文件                            | `/etc/yum.cnf`                                               |
| yum的资源库配置文件                                  | `/etc/yun.repo.d/Centos-Base.repo`                           |
| 安装指定的软件httpd                                  | `yum install httpd`                                          |
| 下载指定的rpm包及其所有的依赖,但是不安装             | `yum install httpd --downloadonly --downloaddir=/home/admin/rpms` |
| 安装当前目录已存在的rpm包,而非是从网络上下载并安装   | `yum localinstall lrzsz-0.12.20-36.el7.x86_64.rpm`           |
| 更新所有的软件包                                     | `yum update`  `yum update all`                               |
| 检查资源库的更新信息                                 | `yum check-update`                                           |
| 大规模的更新软件包,并包含本地库中陈旧的软件包        | `yum upgrade`                                                |
| 输出资源库中所有的软件包的信息(非常的不推荐使用)     | `yum info`  `yum info all`                                   |
| 输出指定软件包的信息                                 | `yum info httpd`                                             |
| 输出可更新的软件包的信息                             | `yum info update`                                            |
| 输出已安装的软件包的所有的信息                       | `yum info installed`                                         |
| 输出已安装但是并不在资源库的所有的第三方软件包的信息 | `yum info extras`                                            |
| 输出资源库中所有软件包的列表                         | `yum list`  `yum list all`                                   |
| 输出指定软件包的列表                                 | `yum list httpd`                                             |
| 输出可更新的软件包的所有的列表                       | `yum list update`                                            |
| 输出已安装的软件包的所有的列表                       | `yum list installed`                                         |
| 输出已安装但是不在资源库的所有的第三方的软件包的列表 | `yum list extras`                                            |
| 以特定的字符来匹配指定的软件包是否存在               | `yum search httpd`                                           |
| 以文件名称来匹配搜索指定的软件包是否存在             | `yum provides httpd`                                         |
| 清除rpm的所有缓存                                    | `yum clean`  `yum clean all`                                 |
| 清除rpm的包缓存                                      | `yum clean packages`                                         |
| 清除rpm的头缓存                                      | `yum clean headers`                                          |
| 清除rpm的旧头缓存                                    | `yum clean oldheaders`                                       |
| 删除指定的软件包                                     | `yum remove httpd`                                           |
| 自动删除本地多余且无用的依赖包                       | `yum autoremove`                                             |
| 输出资源库的配置列表                                 | `yum repolist`                                               |
| 输出资源库的配置信息                                 | `yum repoinfo`                                               |
| 本地生成资源库的缓存数据                             | `yum makecache`                                              |
| 查看yum的操作历史                                    | `yum history`                                                |

# 手动安装软件包记录

| 关键字            | 简述                                           |
| ----------------- | ---------------------------------------------- |
| `lrzsz`           | windows和linux传输文件工具                     |
| `elinks`          | linux下的文本浏览器                            |
| `wegt`            | url下载工具                                    |
| `telnet`          | 端口测试工具                                   |
| `traceroute`      | 路由跟踪工具                                   |
| `redhat-lsb`      | OS版本详细信息查看工具                         |
| `man-pages-zh-CN` | man帮助指令汉化包                              |
| `yum-utils`       | yum配置管理工具,常用的指令是yum-config-manager |

# centos配置记录

## 配置中文版的man手册

- `yum install man-pages-zh-CN`  
- `find / -maxdepth 4 | grep -i man/zh_cn`  
- 编辑用户目录中的`.bashrc`文件,添加别名设置:`	alias cman='man -M /usr/share/man/zh_CN'`  
- 重新登陆terminal即可.

## 通用的静态地址配置模板

```
TYPE=Ethernet
BOOTPROTO=static
ONBOOT=yes
IPADDR=192.168.1.129
NETMASK=255.255.255.0
BROADCAST=192.168.1.255
NETWORK=192.168.1.0
GATEWAY=192.168.1.2
DNS1=180.76.76.76
DNS2=114.114.114.114
HWADDR=00:0C:29:D3:24:1B
NAME=ens32	
```

<u>补充说明:1)改方式的配置适用于 `centos6`和 `centos7`;2)若是需要物理网卡的mac地址或者是uuid可以通过 `nmcli`指令查询</u>

## ip别名的配置

更改配置文件的方式(永久生效)

- 在`/etc/sysconfig/network-scripts`目录中,复制当前使用的网卡配置文件,比如`ifcfg-ens33`
- 文件名称要是原名称:x的格式,比如`ifcfg-ens33:0`
- 使用vim更改配置文件中的`name,device,ipaddr`等字段的值
- 重启网卡 `systemctl restart network`
- 查看验证 `ip addr show`

使用ifconifg或ip指令的方式(临时生效)

- 临时添加一个ip别名  `ifconfig ens33:0 add 192.168.1.131 netmask 255.255.25%.0 up`

  或 `ip addr add 192.168.1.131/24 brd + dev ens33 label ens33:0` 

- 删除临时添加的ip别名	`ifconfig ens33:0 del 192.168.1.131`

  或者  `ip addr del 192.168.1.131/24 brd + dev ens33 label ens33:0`

最后进行测试,物理网卡ens33的地址是`192.168.1.129`,添加的别名ip地址是`192.168.1.131`,若生效即可ping通131的地址.

