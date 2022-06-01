1. 下载压缩包到任意目录解压
2. 将目录中的struct.sql导入到MySQL数据库中
3. 修改conf.json.example中的配置并重命名文件为conf.json
4. 如果使用nginx反代的话，请按如下修改配置文件

反代配置文件：
在 **location / {}** 块的 proxy_set_header REMOTE-HOST $remote_addr; 行后加入：
```
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
```

主配置文件：
在 root /www/wwwroot/xxx.com; 行后加入：
```
proxy_http_version 1.1;
```
