- wget
- `cat os-release`
- `cat /proc/cpuinfo `
- `cat /proc/meminfo`
- `cat /proc/version`
- `/proc/uptime` 直接执行
    - ` 08:41:23 up  1:28,  0 users,  load average: 0.42, 0.25, 0.23`
    - 当前系统时间是早上 8 点 41 分 23 秒。
    - 系统自从上次启动以来已经运行了 1 小时 28 分钟。
    - load average: 0.42, 0.25, 0.23 表示系统在过去 1 分钟、5 分钟和 15 分钟内的平均负载
- `netstat -an|grep :8080`

### 换源
https://github.com/RubyMetric/chsrc