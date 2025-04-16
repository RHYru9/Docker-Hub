### Docker部署云vscode编辑器

创建项目文件
```
mkdir -p code-server && cd code-server && touch docker-compose.yaml
```



`docker-compose.yaml`配置

```
services:
  code-server:
    image: linuxserver/code-server:latest
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Shanghai
      - PASSWORD=admin123      # 设置 code-server 的登录密码
      - SUDO_PASSWORD=         # 设置服务器 sudo 权限的密码（可选）
    volumes:
      - ./code-server/config:/config    # 挂载配置文件
    ports:
      - 8443:8443
    restart: always
```





[官方文档](https://docs.linuxserver.io/images/docker-code-server/)


#### 挂载服务器根目录和赋予容器root权限

- 此配置将赋予容器最高权限，服务器所有的文件都可读写可修改（生产环境慎重使用）

```
services:
  code-server:
    image: linuxserver/code-server:latest
    container_name: code-server
    environment:
      - PUID=0
      - PGID=0
      - TZ=Asia/Shanghai
      - PASSWORD=admin123ASD789@      # 设置code-server的登录密码（建议强密码）
      - SUDO_PASSWORD=                # 设置服务器sudo权限的密码（可选）
    volumes:
      - /:/config/workspace           # 宿主机根目录设置为工作目录
    ports:
      - 8443:8443
    privileged: true
    cap_add:
      - ALL
    security_opt:
      - seccomp:unconfined
      - apparmor:unconfined
    restart: always
```

