## 直播和观影平台synctv

```
docker run -d --name synctv -p 8080:8080 synctvorg/synctv:latest
```

默认管理员账户：
```
root
```
```
root
```

[官方地址](https://github.com/synctv-org/synctv)



如果你想改前端文件，需要clone前端项目，然后修改，编译出前端文件

然后运行docker的时候映射编译好的前端文件：`-v /路径/dist:/dist`，同时添加环境变量`-e WEB_PATH=/dist`


例如：
```
docker run -d --name synctv -p 8080:8080 -e WEB_PATH=/dist -v /路径/dist:/dist synctvorg/synctv:latest
```


