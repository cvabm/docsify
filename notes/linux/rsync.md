# rsync

`rsync`是一个用于同步文件和目录的强大工具，它可以通过本地或远程传输数据。`rsync`通常用于备份和镜像，但也可以用于日常文件同步任务。以下是一些基本的`rsync`使用例子：

### 本地同步

将本地目录同步到另一个本地目录：

```
bash复制
rsync -av /source/directory/ /destination/directory/
```

这里，`/source/directory/`是源目录，`/destination/directory/`是目标目录。

### 排除文件

在同步时排除某些文件或目录：

```
bash复制
rsync -av --exclude 'pattern' /source/directory/ /destination/directory/
```

例如，排除所有`.tmp`文件和`cache`目录：

```
bash复制
rsync -av --exclude='*.tmp' --exclude='cache' /source/directory/ /destination/directory/
```

### 远程同步

将本地目录同步到远程服务器：

```
bash复制
rsync -avz /source/directory/ username@remotehost:/destination/directory/
```

这里，`username`是远程服务器的用户名，`remotehost`是远程服务器的地址。

### 同步远程目录到本地

将远程服务器上的目录同步到本地：

```
bash复制
rsync -avz username@remotehost:/remote/directory/ /local/directory/
```

### 仅同步文件变更

仅同步有变更的文件，不重新传输未更改的文件：

```
bash复制
rsync -av --delete /source/directory/ /destination/directory/
```

这里的`--delete`选项会删除目标目录中源目录不存在的文件。

### 压缩数据

在传输过程中压缩数据以节省带宽：

```
bash复制
rsync -avz /source/directory/ /destination/directory/
```

`-z`选项会在传输过程中压缩文件数据。

### 保留文件权限和属性

同步文件时保留原有的权限和时间戳：

```
bash复制
rsync -avog /source/directory/ /destination/directory/
```

这里的`-o`保留文件所有权，`-g`保留群组信息，`-t`保留时间戳。

### 同步到USB设备

将文件同步到挂载的USB设备：

```
bash复制
rsync -av --progress /source/directory/ /media/usb/
```

### 同步时保留硬链接

使用`-H`选项来保留硬链接：

```
bash复制
rsync -avH /source/directory/ /destination/directory/
```

### 同步时保留文件的追加属性

使用`--append-verify`选项来在同步后进行校验：

```
bash复制
rsync -av --append-verify /source/directory/ /destination/directory/
```

### 使用SSH进行加密传输

通过SSH进行加密传输：

```
bash复制
rsync -av -e ssh /source/directory/ username@remotehost:/destination/directory/
```

在使用`rsync`时，`-a`（归档模式）通常是一个有用的选项，因为它保留了原始文件的权限、时间戳、软硬链接等。而`-v`（详细模式）和`--progress`（显示进度）可以帮助你更好地了解同步过程。始终建议查看`rsync`的手册页（通过运行`man rsync`）以了解更多高级选项和使用技巧。