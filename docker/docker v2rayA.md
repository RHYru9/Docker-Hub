### Liunx系统代理工具V2rayA

```
docker run -d \
  --restart=always \
  --privileged \
  --network=host \
  --name v2raya \
  -e V2RAYA_LOG_FILE=/tmp/v2raya.log \
  -e V2RAYA_V2RAY_BIN=/usr/local/bin/v2ray \
  -e V2RAYA_NFTABLES_SUPPORT=off \
  -e IPTABLES_MODE=legacy \
  -v /lib/modules:/lib/modules:ro \
  -v /etc/resolv.conf:/etc/resolv.conf \
  -v /etc/v2raya:/etc/v2raya \
  mzz2017/v2raya
```

web面板地址：`http://公网IP:2017`


#### 环境变量
```
export http_proxy=socks5://127.0.0.1:20170
export https_proxy=socks5://127.0.0.1:20170
```
默认情况下 v2rayA 会通过内核开放 20170(socks5), 20171(http)


#### 透明代理配置

![alt](/png/touming.jpg)
