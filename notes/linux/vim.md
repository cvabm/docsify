# vim

## vim 常用命令

- 基本
    - `vim test.txt`
    - `:wq` 保存并退出
    - `:q!` 不保存强制退出
- 插入
    - `i`文字前插入
    - `a`文字后插入
    - `o` 在文本底下插入一行
    - `O` 在当前行之上新开一行
- 删除
    - `x` 删除光标所在字符
    - `X` 删除光标前字符
    - `dd` 删除文字所在整一行
    - `ndd` 删除 n 行
    - `dw` 删除单词
    - `Ctrl+u` 删除输入方式下所输入的文本
- 复制黏贴
    - `v` 移动选择文本
    - `y` 复制
    - `p` 黏贴
    - `yy`复制当前一行
    - `nyy` 复制 n 行,类推
- 撤回
    - `u`
    - `U`
- `:e ++enc=utf8:e ++enc=gbk`
- 移动/翻页
    - `0` 行首
    - `$` 行尾
    - `gg` 首行
    - `G` 最后一行
    - `:nu` 跳到第 nu 行
    - `10G` 跳转到第10行，跟:nu一样效果
    - `10%` 跳转到文档10%进度
    - `Ctrl+u` 上半页
    - `Ctrl+d` 下半页
    - `Ctrl+f` 下一页
    - `Ctrl+b` 上一页
    - `[[` 返回文本开始
    - `]]` 到达文本末尾
    - `w` 光标右移一个字至字首
    - `b` 光标左移一个字至字首
    - `e` 光标右移一个字至字尾
- 查找
    - `/关键字` 回车
    - `n` 下一个
    - `N` 上一个
    - `:find dir/a.txt`文本内搜索其他文件
- 行号
    - `:set nu` 行号
- 修改属性
    - `chmod +777 文件名`
- 文件切换
    - `ctrl ^`
    - `:ls` 列出已打开文件
    - `:e 文件名`
- 分屏
    - `:sp` 上下分屏
    - `:vsp` 左右
    - `:q` 关闭某一屏
    - `Ctrl w` 按两次或按一次+hjkl 切屏
- 禁止生成临时文件

```
set nobackup       " no backup files
set noswapfile     " no swap files
set nowritebackup  " only in case you don't want a backup file while editing
set noundofile     " no undo files

```

- 其他
    - `syntax on` 语法高亮

## vim 配色

[https://github.com/NLKNguyen/papercolor-theme](https://github.com/NLKNguyen/papercolor-theme)

## windows 命令

- `taskmgr` 任务管理器
- `shutdown -s -t 1200` //在两分钟后关闭计算机
- `shutdown /a` //取消关机命令
- `start notepad "c:\\test.txt"` 指定记事本打开
- `start chrome baidu.com`
- `start 文件或文件夹`（直接打开）
- `touch file` 新建文件
- `systeminfo` 查看系统信息
- ``echo -e "第一行\\n第二行\\n第三行" > 111.txt` 输入文本到txt
