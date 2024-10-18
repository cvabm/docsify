# docker

## 常用命令
1. **启动 Docker 服务**：

   ```
   sudo systemctl start docker
   ```

2. **查看 Docker 版本**：

   ```
   docker --version
   ```

3. **拉取镜像**：

   ```
   docker pull image_name:tag
   ```

4. **运行容器**：

   ```
   docker run [OPTIONS] image [COMMAND] [ARG...]
   ```

5. **列出所有运行中的容器**：

   ```
   docker ps
   ```

6. **列出所有容器（包括未运行的）**：

   ```
   docker ps -a
   ```

7. **停止容器**：

   ```
   docker stop container_id_or_name
   ```

8. **启动已停止的容器**：

   ```
   docker start container_id_or_name
   ```

9. **强制停止容器**：

   ```
   docker kill container_id_or_name
   ```

10. **删除容器**：

    ```
    docker rm container_id_or_name
    ```

11. **删除镜像**：

    ```
    docker rmi image_id_or_name
    ```

12. **查看容器日志**：

    ```
    docker logs container_id_or_name
    ```

13. **进入运行中的容器**：

    ```
    docker exec -it container_id_or_name /bin/bash
    ```

14. **构建镜像**：

    ```
    docker build -t image_name:tag path_to_Dockerfile
    ```

15. **查看镜像列表**：

    ```
    docker images
    ```

16. **导出镜像**：

    ```
    docker save -o image_name.tar image_name:tag
    ```

17. **导入镜像**：

    ```
    docker load -i image_name.tar
    ```

18. **创建网络**：

    ```
    docker network create network_name
    ```

19. **删除网络**：

    ```
    docker network rm network_name
    ```

20. **查看 Docker 容器的 IP 地址**：

    ```
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name
    ```

21. **清理未使用的资源**：

    ```
    docker system prune
    ```

22. **查看容器的资源使用情况**：

    ```
    docker stats
    ```

23. **更新容器为最新镜像**：

    ```
    docker update --upgrade container_name
    ```

24. **重启 Docker 服务**：

    ```
    sudo systemctl restart docker
    ```

25. **查看容器的详细信息**：

    ```
    docker inspect container_id_or_name
    ```

这些命令覆盖了 Docker 的基本操作，包括容器的启动、停止、删除，镜像的拉取、构建、删除等。

### 通过docker overlay2 目录名查找对应容器名

```
cd /var/lib/docker/overlay2/
查看容器占用大小
du -s ./* | sort -rn | more
通过目录名查找容器名
docker ps -q | xargs docker inspect --format '{{.State.Pid}}, {{.Id}}, {{.Name}}, {{.GraphDriver.Data.WorkDir}}' | grep bff25099a59b0fc8addd06f9223872f2904256f0432b3c3c47b58faef167115f
```

## docker命令

```
docker启动命令,docker重启命令,docker关闭命令

启动        systemctl start docker

守护进程重启   sudo systemctl daemon-reload

重启docker服务   systemctl restart  docker

重启docker服务  sudo service docker restart

关闭docker service docker stop

关闭docker systemctl stop docker
```