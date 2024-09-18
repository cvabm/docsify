## github
## fork 项目不可使用 GITHUB_TOKEN 的问题

报错 Resource not accessible by integration

解决：项目- settings -actions - General - Workflow permissions -Read and write

## github 配置 ssh

- 第一步：检查本地主机是否已经存在 ssh key

```bash
cd ~/.sshls//看是否存在 id_rsa 和 id_rsa.pub文件，如果存在，说明已经有SSH Key
```

- 第二步：生成 ssh key

```bash
如果不存在 ssh key，使用如下命令生成ssh-keygen -t rsa -C "xxx@xxx.com"//执行后一直回车即可
```

- 第三步：获取 ssh key 公钥内容（id_rsa.pub）

```bash
cd ~/.sshcat id_rsa.pub复制该内容
```

- 第四步：Github 账号上添加公钥

```
进入 Settings 设置
添加 ssh key，把刚才复制的内容粘贴上去保存即可
```

- 第五步：验证是否设置成功

```bash
ssh -T git@github.com
```