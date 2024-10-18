## windows
### 常用命令

- `start .`或者`explorer .`打开当前路径的文件夹
- `df -h` disk free
- `tasklist | findstr "nginx"` 查看某服务是否运行
- `taskkill /F /IM nginx.exe` 停止服务
- `taskkill /F /PID 118028`
- `shift+滚动` 左右滚动网页

### windows/问题

- **“ipconfig 不是内部命令或外部命令”解决方法**

配置环境变量

Path 加入内容“c:\windows\system32”

### ****WIN10蓝屏终止代码：inaccessible boot device解决办法****

[https://zhuanlan.zhihu.com/p/519845612?utm_id=0](https://zhuanlan.zhihu.com/p/519845612?utm_id=0)

### 蓝牙鼠标休眠导致卡死问题

- 右键点击开始菜单，打开设备管理器，找到蓝牙，右键点击 英特尔 无线 Bluetooth ，打开属性。
- 在 电源管理 选项卡上, 取消选中 “允许计算机关闭此设备以节省电源” 选项，保存即生效。不是所有蓝牙模块都有电源管理选项，没有这个选项的一般也不会自动关闭。


### 打包exe程序
- exe4j jar打包成exe
- 



### wsl使用

[https://zhuanlan.zhihu.com/p/36482795](https://zhuanlan.zhihu.com/p/36482795)

- **windows cmd 改编码**

```

将当前控制台编码设置为 UTF-8，则输入
chcp 65001
chcp 936
通过 CHCP 设置编码是治标不治本的
想永久的更改 cmd 编码值需要修改注册表
方法一：
在运行中通过 regedit 进入注册表
找到 HKEY_CURRENT_USER\\Console\\%SystemRoot%\\_system32_cmd.exe
新建一个 DWORD（32 位值）,命名为 CodePage，值设为 65001
已有 CodePage 的话，修改它，改为十进制，65001

```

### windows 查看文件被占用进程

打開“資源監視器”。在“資源監視器”界面中，點擊第二個選項卡“CPU”。在“關聯的句柄”右側搜索框內輸入文件名稱，就可以查看該文件被那幾個程序佔用了。

![查看文件占用.jpeg](images/查看文件占用.jpeg)

### 宏碁 u 盘启动

```

1、开机按 F2 进入 bios 设置界面，然后切换到“boot”栏，移动光标选择“Boot priority order”按回车确定。
2、想要使用快捷键 U 盘启动的用户，完成步骤三操作后，开机按 F12 再选择 U 盘启动即可。

```

### win10 删除多余的系统引导

```

1、按 Win+R 键打开运行，输入 cmd 回车进入命令提示符。
2、在命令提示符下输入 msconfig,然后回车。
3、此时跳出系统配置的窗口，点击引导选项卡。
4、进入引导选项，在里面可以看到本计算机所有的引导，第一个是当前系统的引导，不能删也无法删，下面的是其他系统的引导，选择要删除的引导删除即可（注意：删除引导意味着该引导下的系统无法再次启动，请确认该引导完全无用后在删除）。

```

- `eventvwr`：事件查看器
- `notepad`：打开记事本
- `osk`：打开屏幕键盘
- `regedit`：注册表
- `snippingtool`：截图工具，支持无规则截图
- `taskmgr`：任务管理器（旧版）

### 校验 md5 值、sha1 等
```

certutil -hashfile xxx MD5
certutil -hashfile xxx SHA1
certutil -hashfile xxx SHA256

```