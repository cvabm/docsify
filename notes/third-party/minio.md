## Android SDK
- 方式一（没进度条）
    demo:https://github.com/cvabm/MinioForAndroid
- 方式二(有进度条)
    demo:引用aws的库，暂无

    - 开始上传文件时，此文件禁止修改。不然报错
    - 使用
    ```js

    列出桶中文件列表，并删除
    val objectListing = s3.listObjects(BUCKET_NAME)
    // 打印对象名称
    val objectSummaries = objectListing.objectSummaries
    objectSummaries.forEach { summary ->
    LogUtils.e(summary.key)
    s3.deleteObject(BUCKET_NAME,summary.key)
    }

    删除桶
    s3.deleteBucket(BUCKET_NAME)
    ```
    - 签名版本4建立的桶，不能签名3去删
    - 签名AWS3SignerType建立的桶，删的时候不能带AWS3SignerType
    - 2.21.0的包含s4和s3签名的，默认用s4
    -  S3SignerType: 使用v2版本签名，url有效期支持2年
    -  AWSS3V4SignerType: 使用v4版本签名，url有效期最大支持7天
    -  中国（北京）：cn-north-1
    -  中国（宁夏）：cn-northwest-1

## window客户端
- mc工具下载 https://dl.min.io/client/mc/release/windows-amd64/mc.exe
- 使用
    ```

    添加服务器
    mc config host add minio http://xxxx:9500 username password

    查看host列表
    mc config host list

    查看minio的桶（minio名称从上述host获取）
    mc ls minio

    查看桶内文件列表
    mc ls minio/capture-screen
    -----------------------------------------------------
    创建桶
    mc mb minio/bucket

    删除桶
    mc rb minio/bucket  -空桶
    mc rb minio/bucket --force  -有文件强制删除

    删除桶内文件
    mc rm minio/bucket/hosts
    删除桶内目录
    mc rm minio/bucket/etc --recursive --force
    -----------------------------------------------------

    上传文件
    mc cp E:\log.txt minio/bucket

    下载文件
    mc cp minio/bucket/log.txt E:\log  到目录
    mc cp minio/bucket/log.txt E:\log111.txt  到目录并改名
    
    上传目录到桶
    mc cp /myfolder minio/bucket --recursive

    查看仓库是否是public
    mc anonymous get minio/bucket

    设置权限
    mc anonymous set public minio/bucket
    ```
    ```
     常用命令
    ls       列出文件和文件夹。
    mb       创建一个存储桶或一个文件夹。
    cat      显示文件和对象内容。
    pipe     将一个STDIN重定向到一个对象或者文件或者STDOUT。
    share    生成用于共享的URL。
    cp       拷贝文件和对象。
    mirror   给存储桶和文件夹做镜像。
    find     基于参数查找文件。
    diff     对两个文件夹或者存储桶比较差异。
    rm       删除文件和对象。
    events   管理对象通知。
    watch    监视文件和对象的事件。
    policy   管理访问策略。
    config   管理mc配置文件。
    update   检查软件更新。
    version  输出版本信息。
    ```

    参考文档：
    https://min.io/docs/minio/linux/reference/minio-mc.html
