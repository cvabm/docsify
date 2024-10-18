# linux
## 网络工具
- `ping`
- `ifconfig`
- `whois`
- `curl -o file.zip https://xxxx` 下载文件 
- `ssh`
- `telnet`
- `ftp/sftp`
- `scp`
- [wget](/notes/linux/wget.md)
- `rsync` [文件夹备份和同步](/notes/linux/rsync.md)
- `ngrep`
- `tcpdump`
- `wireshark`
- `tshark` wireshark的命令行工具
- `openvpn`
- `nmap` 网络扫描工具
- `iptables` 配置网络防火墙
- `nc` 监听 TCP 和 UDP 端口，发送和接收数据，以及建立简单的连接
- `socat`
- `netstat`
- `openssl`
## 安装和更换 JDK

```
安装jdk 1.6
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java6-installer
切换jdk当前版本
sudo update-alternatives --config java
vi .bashrc
export PATH=/usr/lib/jvm/java-1.6.0-openjdk-amd64/bin:$PATH
推荐JDK版本：OpenJDK 1.7
$ sudo apt-get install openjdk-7-jre openjdk-7-jdk
<intent-filter>
<action android:name="com.cibn.browser" />
<category android:name="android.intent.category.DEFAULT" />
</intent-filter>

```

## ubuntu 更换国内源

[https://zhuanlan.zhihu.com/p/61228593](https://zhuanlan.zhihu.com/p/61228593)
## linux 命令

[https://www.linuxcool.com](https://www.linuxcool.com/)
- `bash zsh fish` 首选bash 比较通用
### 网络

- `ip addr`查看 ip 地址
- `ip -s link`显示不同网络接口的统计数据
- 文件操作
    - `cp` 拷贝 其他
- `chmod 777`最高权限
- `chmod 999`有一定安全性，推荐
- `echo 'abcdef' > gaga.txt`向 gaga.txt 文件里面写入内容 abcdef
- `echo 22 >> gaga.txt` 追加字符
- `df -h /mnt/sdcard` 列出来一个目录的空间状态信息
- `du -h file.ext` 获取文件大小信息
- `sudo apt-get remove` 卸载软件
- `dd if=/dev/zero of=zero_file bs=1M count=1024`全零文件：内容全为零字节，实际占用磁盘空间与文件大小相同。
- `dd if=/dev/urandom of=random_file bs=1M count=1024` 随机数据文件：内容为随机字节，实际占用磁盘空间与文件大小相同。
- `dd if=/dev/zero of=sparse_file bs=1M count=0 seek=1024` 稀疏文件：包含大量零字节，但这些零字节不实际占用磁盘空间，实际占用空间远小于文件大小。
- `ls -1a` 查看包含隐藏文件
- `ps -e` 显示所有进程
- `ps -ef` 所有进程的详细信息
- `ps -ef|grep dockerd` 查看某进程信息
- `pwd` 显示当前路径
- `cd –` 返回上一次目录
- `cd ~` 返回主目录
- `cd /` 返回根目录
- `shutdonw -h now & half & poweroff` 关机
- `cat` 由第一行开始显示 cat |more 分页
- `less` 可翻页看文档
- `head -n` 文档前n行
- `nl` 在内容前加行号
- `whereis`,`locate` 快速定位查找
- `find 查找 find / -name “**_._**”`详细查找
- `whoami` 显示当前用户
- `free` 显示内存状态 free -m —>以 M 为单位显示
- `netstat` 显示网络状态 netstat -tulnp–>找出目前系統上已在監聽的網路連線及其 PID
- `tar -cvf /home/123.tar /etc` 打包，不压缩
- `tar -xvf 123.tar`解开包
- `dpkg` 安装、卸载、管理软件工具
- `dpkg -l` 查看已安装
- `apt-get` 
- `apt` 新的包管理工具 -更简洁
- `diff 1.txt 2.txt`比较
### 文本
#### less|more|tail|vim|区别
- less 只查看，大文件加载比vim快
    - `f`前进 `b`后退  `q`退出
    -  `/`搜索 n下一个搜索位置 N上一个
- cat 打印查看文档内容
- tail 实时监控日志，tail -f filename.txt ，默认后10行，-n 20，指定20行
- nano 简单文本，初学者
- `grep key log.txt` 找出包含key的语句
- awk
- sed
    - `sed 's/w/发/g' q.txt > qq.txt` 全局替换w > 发
    - `sed -i 's/w/发/g' q.txt` 直接改文件
- watch
### 文件
- `gzip` 压缩单个文件 [gzip使用](./gzip.md)
- `gunzip`
- `zip` 压缩多个文件
- `unzip`
- `tar` 只打包，不压缩
- `jq` 
    - `jq -n '{name: "Alice", age: 30}' > output.json` 生成文件
    - `jq . test.json` 格式化预览输出到终端
    - `jq -c . test.json` 压缩一行预览
    - `jq . test.json > format.json` 格式化到另一个文件
- `tree` 树形列表展示路径和子文件，可设深度
### 进程
- `top` 实时的系统监控信息，包括 CPU 使用率、内存使用情况、运行的进程等。
- `htop` top的增强版
- `passwd` 更改密码
## 常见问题
    - ubuntu 安装依赖：0.8.1-1ubuntu4.4 正要被安装 解决办法： 进入“系统->系统管理->更新管理器->设置”，在弹出的“软件源”对话框中选“更新”标签页，选中“Ubuntu 更新”下面的四个复选框，关闭后 四个权限都打开 在终端先执行“sudo apt-get update”就 ok 了
    - Could not get lock /var/lib/apt/lists/lock 执行 sudo rm /var/lib/apt/lists/lock


## xshell 上传下载

- `ssh user@ip port` user可为root
- `rz -y`
- `sz file`
- `yum install lrzsz`
## 抓包
- `ifconfig` 获取网卡名 ，比如如eno2
-  `tcpdump -i eno2 -w temp.pcap`
-  sz temp.pcap
## linux 拷贝文件

- `scp -r /home/shaoxiaohu/test1 zhidao@192.168.0.1:/home/test2` 本机->远程服务器 test1 为源目录，test2 为目标目录，zhidao@192.168.0.1为远程服务器的用户名和 ip 地址。
- `scp -r zhidao@192.168.0.1:/home/test2 /home/shaoxiaohu/test1` Linux 下目录复制：远程服务器->本机 zhidao@192.168.0.1为远程服务器的用户名和 ip 地址，test1 为源目录，test2 为目标目录。

注：如果端口号有更改，需在 scp 后输入：-P 端口号 （注意是大写，ssh 的命令中 -p 是小写

### linux 翻墙

```
执行 `cd && mkdir clash` 在用户目录下创建 clash 文件夹。

下载适合的 Clash 二进制文件并解压重命名为 `clash`

一般个人的 64 位电脑下载 clash-linux-amd64.tar.gz 即可。

[下载客户端](<https://github.com/Dreamacro/clash/releases>)

```

- 
    
    在终端 `cd` 到 Clash 二进制文件所在的目录，执行 `wget -O config.yaml <https://www.paopaoyunyi.top/link/xxxxxxxxxx`> 下载 Clash 配置文件
    
    [复制 wget 命令](https://www.ppyu.top/user/tutorial?os=linux&client=clash##)
    
    ![https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-2.jpg](https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-2.jpg)
    
- 
    
    执行 `./clash -d .` 即可启动 Clash，同时启动 HTTP 代理和 Socks5 代理。
    
    如提示权限不足，请执行 `chmod +x clash`
    
    ![https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-3.jpg](https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-3.jpg)
    
- 
    
    访问 [Clash Dashboard](http://clash.razord.top/) 可以进行切换节点、测延迟等操作。
    
    Host: `127.0.0.1`，端口: `9090`
    
    ![https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-4.jpg](https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-4.jpg)
    
- 
    
    以 Ubuntu 19.04 为例，打开系统设置，选择网络，点击网络代理右边的 ⚙ 按钮，选择手动，填写 HTTP 和 HTTPS 代理为 `127.0.0.1:7890`，填写 Socks 主机为 `127.0.0.1:7891`，即可启用系统代理。
    
    ![https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-5.jpg](https://www.ppyu.top/theme/malio/img/tutorial/linux-clash-5.jpg)
    

### 电脑键盘注册表已损坏导致无法输入信息的修复方式

解决方法：

1、打开注册表 regedit

注意： 如果因为键盘无法输入， 无法**W+R**打开运行窗口 输入 **regedit**

可以在以下目录中点击 **regedit.exe** 执行

```bash
C:\\Windows\\regedit.exe

```

![https://img-blog.csdnimg.cn/db017430930242f88e46b83b86df222a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16](https://img-blog.csdnimg.cn/db017430930242f88e46b83b86df222a.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16)

在这里插入图片描述

2、定位到目录，删除 UpperFilters 项，并返回设备管理器中卸载设备，重新启动。

```bash
HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Class\\{4D36E96B-E325-11CE-BFC1-08002BE10318}

```

![https://img-blog.csdnimg.cn/20035f2d1ee940348e1f65a1bfb03e30.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16](https://img-blog.csdnimg.cn/20035f2d1ee940348e1f65a1bfb03e30.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16)

在这里插入图片描述

此时可能出现两种情况

- 设备管理器里变成：代码 10：该设备无法启动。
- 这个设备运转正常（如图 5 一样），但依然输入无效。

3、重新定位到目录 ，右键右边的空白处，新建字符串，数值名称是**UpperFilters**项，数值数据是**kbdclass**

```bash
HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Class\\{4D36E96B-E325-11CE-BFC1-08002BE10318}

```

![https://img-blog.csdnimg.cn/cb3db6cdaa95432b9b8e7cfa949785ca.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_18,color_FFFFFF,t_70,g_se,x_16](https://img-blog.csdnimg.cn/cb3db6cdaa95432b9b8e7cfa949785ca.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_18,color_FFFFFF,t_70,g_se,x_16)

在这里插入图片描述

庆幸提前安装好 QQ，还能扫码登陆发送文字 **kbdclass** 复制粘贴过去就行。

4、返回设备管理器卸载设备，重新启动，就能正常使用。

![https://img-blog.csdnimg.cn/25165eb746df4cd4bed7e4a736e34416.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16](https://img-blog.csdnimg.cn/25165eb746df4cd4bed7e4a736e34416.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBA5qKm5Yed5ZOy6Zuq,size_20,color_FFFFFF,t_70,g_se,x_16)

---

### linux 依赖解决办法

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```

second step

```
sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove

```

third step

```
sudo apt --fix-broken install
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f

```

### Ubuntu20.04 安装 yum 报错【无法定位软件包 yum】解决

**终极解决办法：**

```bash
#备份sources.list文件sudo cp  /etc/apt/sources.list /etc/apt/sources.list.bak#打开sources.list文件sudo vim  /etc/apt/sources.list#删除原内容，添加下列内容deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic main restricted universe multiversedeb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic main restricted universe multiversedeb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-updates main restricted universe multiversedeb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-updates main restricted universe multiversedeb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-backports main restricted universe multiversedeb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-backports main restricted universe multiversedeb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-security main restricted universe multiversedeb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-security main restricted universe multiversedeb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-proposed main restricted universe multiversedeb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-proposed main restricted universe multiversedeb <http://mirrors.aliyun.com/ubuntu/> bionic main restricted universe multiversedeb <http://mirrors.aliyun.com/ubuntu/> bionic-security main restricted universe multiversedeb <http://mirrors.aliyun.com/ubuntu/> bionic-updates main restricted universe multiversedeb <http://mirrors.aliyun.com/ubuntu/> bionic-proposed main restricted universe multiversedeb <http://mirrors.aliyun.com/ubuntu/> bionic-backports main restricted universe multiversedeb-src <http://mirrors.aliyun.com/ubuntu/> bionic main restricted universe multiversedeb-src <http://mirrors.aliyun.com/ubuntu/> bionic-security main restricted universe multiversedeb-src <http://mirrors.aliyun.com/ubuntu/> bionic-updates main restricted universe multiversedeb-src <http://mirrors.aliyun.com/ubuntu/> bionic-proposed main restricted universe multiversedeb-src <http://mirrors.aliyun.com/ubuntu/> bionic-backports main restricted universe multiverse#保存 做完以上前期工作，正式安装yumsudo apt-get updatesudo apt install yum#成功解决上楼报错

```

### Alacritty 命令行工具

Alacritty 默认不会添加配置文件，需要自己手动添加。

- Linux & Mac

```
~/.config/alacritty/alacritty.yml

```

- Windows

```
%APPDATA%\\alacritty\\alacritty.yml

```

[配色 1](https://github.com/alebelcor/alacritty-snazzy)

### 检测服务端口是否打开
```
ssh -v 127.0.0.1 -p 80
打印Connection established. 则打开了
echo >/dev/tcp/127.0.0.1/80
```
