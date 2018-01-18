## Nginx Proxy PHP

使用jwilder的nginx-proxy镜像，加入了PHP-FastCGI的支持，使用方法与[nginx-proxy](https://github.com/jwilder/nginx-proxy)大同小异。

### PHP-FastCGI 配置办法

可使用以下docker-compose配置进行启动，单行命令启动请各位自行领会。（手动滑稽）

```yaml
version: '2'
services:
  nginx-proxy:
    image: gsgtzq/nginx-proxy-php:latest
    container_name: nginx-proxy
    ports:
      - "80:80"
    volumes:
      - /var/run/docker.sock:/tmp/docker.sock:ro
      - ./path/to/your/app:/var/www/html
  www.yourhost.com:
    image: gsgtzq/php:7.1-fpm
    container_name: www.yourhost.com
    volumes:
      - /path/to/your/app:/var/www/html/page
    environment:
      - VIRTUAL_HOST=www.yourhost.com
      - VIRTUAL_PROTO=fastcgi
      - APP_LOCATION=/var/www/html
```

### 不完善的地方

- 端口号只支持80，碍于对Golang模板语法不熟，暂时改不了，有熟悉的朋友，欢迎PR。