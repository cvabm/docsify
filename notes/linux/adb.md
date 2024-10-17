# adb
## adb 工具 webadb

[https://yume-chan.github.io/ya-webadb/](https://yume-chan.github.io/ya-webadb/) 浏览器 adb 连接手机，必须关闭 studio 等其他 adb 程序 [https://www.vysor.io/](https://www.vysor.io/) 下载 windows 版本即可跟 android studio 共存

## adb 命令

[https://github.com/mzlogin/awesome-adb](https://github.com/mzlogin/awesome-adb)

- `adb shell pm list packages`：列出设备上安装的所有应用程序包名。

| 参数 | 显示列表 |
| --- | --- |
| 无 | 所有应用 |
| -f | 显示应用关联的 apk 文件 |
| -d | 只显示 disabled 的应用 |
| -e | 只显示 enabled 的应用 |
| -s | 只显示系统应用 |
| -3 | 只显示第三方应用 |
| -i | 显示应用的 installer |
| -u | 包含已卸载应用 |
| <FILTER> | 包名包含 <FILTER> 字符串 |
- `adb shell input text <text>`：模拟输入指定文本。
- `adb install` 后面可以跟一些可选参数来控制安装 APK 的行为，可用参数及含义如下：

| 参数 | 含义 |
| --- | --- |
| -l | 将应用安装到保护目录 /mnt/asec |
| -r | 允许覆盖安装 |
| -t | 允许安装 AndroidManifest.xml 里 application 指定 android:testOnly="true" 的应用 |
| -s | 将应用安装到 sdcard |
| -d | 允许降级覆盖安装 |
| -g | 授予所有运行时权限 |
| –abi abi-identifier | 为特定 ABI 强制安装 apk，abi-identifier 可以是 armeabi-v7a、arm64-v8a、v86、x86\_64 等 |
- `adb reboot`：重新启动设备。
- `adb shell am start -n <package_name>/<activity_name>`：启动指定应用程序的活动。
- `adb shell am startservice -n <service_name>`：启动指定服务。
- `adb shell am force-stop <package_name>`：强制停止指定应用程序。
- `adb shell am force-stop <package_name>`：强制停止指定应用程序。
- `adb shell am kill <package_name>`：杀死指定应用程序的进程。
- `adb shell dumpsys package <package_name>`：显示指定应用程序的包信息。
- 

### 查看正在运行的 Services

命令：

```css
adb shell dumpsys activity services [<packagename>]

```

`<packagename>` 参数不是必须的，指定 `<packagename>` 表示查看与某个包名相关的 Services，不指定表示查看所有 Services。

`<packagename>` 不一定要给出完整的包名，比如运行 `adb shell dumpsys activity services org.mazhuang`，那么包名 `org.mazhuang.demo1`、`org.mazhuang.demo2` 和 `org.mazhuang123` 等相关的 Services 都会列出来。

- `adb shell wm density`：设置设备的屏幕密度。
- `adb -s cf264b8f shell wm size` 获取屏幕分辨率
- `adb shell screencap <file_path>`：截屏，并将截图保存到指定的文件路径。
- `adb pull <device_file_path> <local_path>`：将设备上的文件复制到本地计算机。
adb pull /system/app/Chrome/Chrome.apk hello123.apk
- `adb push <local_path> <device_file_path>`：将本地计算机上的文件复制到设备上。
- `adb bugreport`：生成设备的 bug 报告，并将其保存到本地计算机。

monkey

- `monkey -p com.itheima.dialog 1000`
- `adb shell monkey -p com.example.agsdkdemo 10000 -s500 -v`
- `adb shell monkey -v -v -v -s 8888 --throttle 300 --pct-touch 30 --pct-motion 25 --pct-appswitch 25 --pct-majornav 5 --pct-nav 0 --pct-trackball 0 -p com.wwdy.app 10000`
- `adb shell monkey -p com.corerate.cep --throttle 500 --ignore-crashes --ignore-timeouts --ignore-security-exceptions --ignore-native-crashes --monitor-native-crashes -s 800 -v -v -v 200000>d:\\111.txt`

stop monkey

- `adb shell ps |grep monkey`
- `adb shell kill pid`

自动化测试

- `adb shell am instrument -w com.example.agsdkdemo.test/android.test.InstrumentationTestRunner`

获取手机信息

- `adb shell getprop | grep product`获取厂商机型
- `adb shell getprop ro.build.version.release`获取 android 版本
- `adb shell getprop ro.product.cpu.abilist`
- `adb shell getprop ro.product.cpu.abi`获取设备硬件信息

input

- `adb shell input keyevent <key_code>`：模拟按下指定的按键。
- `adb shell input keyevent 26 && adb shell input swipe 250 250 800 800`：解锁手机
- 空格：`adb shell input keyevent 62`
- 删除：`adb shell input keyevent 67`
- MENU：`adb shell input keyevent 1`
- HOME：`adb shell input keyevent 2`
- back：`adb shell input keyevent 3`
- 字符：`adb shell input text ‘hello,world’`
- `adb reverse tcp:8081 tcp:8081` Android 允许我们通过 ADB，把 Android 上的某个端口映射到电脑（adb forward），或者把电脑的某个端口映射到 Android 系统（adb reverse）。 假设电脑上开启的服务，监听的端口为 8000。Android 手机通过 USB 连接电脑后，执行 adb reverse tcp:8000 tcp:8000，然后在手机中访问 127.0.0.1:8000，就可以访问到电脑上启动的服务了。
- `adb shell am start -W [app包名]/[activtity路径.launchActivity]`app 启动时间

日志

- `adb logcat | grep "xxxx"`过滤日志，window 把 grep 改为 find
- `adb logcat > logcat/log.txt` 保存 log 到 txt 文件
- `adb logcat -c` ;清除 log
- `adb logcat -d -s ReactNativeJS -v time > redmi.txt` 读完最近所有 log 保存后返回
- `adb logcat -b crash` 过滤崩溃日志
- `adb bugreport`：生成设备的 bug 报告。

apk 管理

- `adb -s emulator-5555 install helloWorld.apk`
- `adb install -r`覆盖已安装
- `adb install -t`允许安装 app-debug.apk 测试包
- `adb -s device_id install 1.apk` 指定设备
- `pm disable PACKAGE_OR_COMPONENT` 冻结应用程序
- `pm enable PACKAGE_OR_COMPONENT` 解冻应用程序

卸载自带软件(免 root)

- `adb shell dumpsys window | grep mCurrentFocus`
- `adb shell pm uninstall -k --user 0 com.qihoo.browser`

清除设备缓存

- `adb shell pm clear <package_name>`
- `adb shell pm uninstall <full.packge.name>`
- `adb shell rm -rf /data/app/<full.package.name>-*`
