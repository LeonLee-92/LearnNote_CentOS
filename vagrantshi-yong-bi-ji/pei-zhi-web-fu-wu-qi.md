### 

### 安装web服务器httpd

```
sudo yum install httpd  // 安装

sudo systemctl start httpd.service    // 启动httpd
systemctl status httpd.service        // 查看httpd状态
```

### web服务器

```
vagrant ssh
yum install httpd
sudo vim  /etc/httpd/conf/httpd.conf  // 如下图
sudo systemctl reload httpd.service
```

![](/assets/import.png)

