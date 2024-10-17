# wget使用
### 基本下载

下载一个文件到当前目录：

```

wget http://example.com/file.txt
```

### 指定输出文件名

下载文件并指定一个不同的文件名：

```

wget http://example.com/file.txt -O downloaded_file.txt
```

### 继续下载

继续一个被中断的下载：

```

wget -c http://example.com/largefile.iso
```

### 限制下载速度

限制下载速度为100KB/s：

```

wget --limit-rate=100k http://example.com/file.txt
```

### 递归下载

递归下载整个网站（注意：这可能会下载很多文件）：

```

wget -r http://example.com/website/
```

### 限制递归深度

递归下载，但限制深度为1：

```

wget -r -l1 http://example.com/website/
```

### 用户代理字符串

设置用户代理（User-Agent）字符串：

```

wget --user-agent="Mozilla/5.0" http://example.com/file.txt
```

### 代理服务器

通过代理服务器下载文件：

```

wget --proxy=on --proxy-server=http://proxyserver:port http://example.com/file.txt
```

### 使用用户名和密码

使用HTTP认证下载文件：

```

wget --user=username --password=password http://example.com/file.txt
```

### 检查证书

忽略服务器SSL证书的验证（不推荐，除非绝对必要）：

```

wget --no-check-certificate https://example.com/securefile.txt
```

### 后台运行

把`wget`放到后台运行，并记录下载进度到文件：

```
wget -b http://example.com/file.txt -O download.log
```

### 指定HTTP方法

使用特定HTTP方法（如HEAD）请求文件：

```
wget --method=HEAD http://example.com/file.txt
```

### 从列表下载

从文本文件中下载一系列URL列表：

```
wget -i urllist.txt
```

### 限制下载文件大小

限制下载的文件大小（例如，小于10MB）：

```

wget --max-filesize=10M http://example.com/largefile.iso
```

在使用`wget`时，可以组合多个选项来满足特定的下载需求。始终建议查看`wget`的手册页（通过运行`man wget`）以了解更多高级选项和使用技巧。

### 递归完整下载
`wget -r -p -np -k [http://xxx.com/xxx](http://xxx.com/xxx)`
- r, --recursive（递归） specify recursive download.（指定递归下载）
-k, --convert-links（转换链接） make links in downloaded HTML point to local files.（将下载的HTML页面中的链接转换为相对链接即本地链接）
-p, --page-requisites（页面必需元素） get all images, etc. needed to display HTML page.（下载所有的图片等页面显示所需的内容）
-np, --no-parent（不追溯至父级） don't ascend to the parent directory.
另外断点续传用-nc参数 日志 用-o参数