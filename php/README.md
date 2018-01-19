## PHP

基于ubuntu16.04加装了ondrej/php的ppa源，PHP版本为7.1，安装了常用的PHP插件。满足快速部署PHP程序。

### Notice

- Linux环境下，需要将应用程序目录所有者修改为`www-data`，否则文件夹不可写会导致程序无法运行。

```bash
sudo chown -R 33:33 /path/to/your/app
```
