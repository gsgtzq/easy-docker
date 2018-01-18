## Mycli Docker
以docker形式封装的mycli，访问docker网络中的MySQL/MariaDB的绝佳助手。

### 使用方法

这里只列出了简单用法，详细的命令可查看[mycli主页](http://www.mycli.net)。

- 启动MySQL

```
docker run -d --name=mysql \
  -p 3306:3306 \
  -e MYSQL_ROOT_PASSWORD=secret \
  mysql:5.7
```

- 启动mycli
```
docker run -it --rm \
  --link mysql:mysql \
  --host mysql \
  --user root \
  --password secret
```

对于在docker环境下的使用，亦可将mycli临时加入到mysql所在网络组中使用，可灵活应用。