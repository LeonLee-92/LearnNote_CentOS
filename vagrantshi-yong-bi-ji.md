### 使用brew分别安装virtralbox和vagrant

### 下载box\(官方仓库Atlas\)

```
vagrant box add [BoxName]
```

### 初始化vagrant项目

    vagrant init [centos/7]

    ->    A `Vagrantfile` has been placed in this directory. You are now
        ready to `vagrant up` your first virtual environment! Please read
        the comments in the Vagrantfile as well as documentation on
        `vagrantup.com` for more information on using Vagrant.

### 一些命令

```
vagrant status    // 查看状态
vagrant up        // 启动
vagrant halt        // 关闭
vagrant suspend    // 暂停
vagrant resume    // 恢复
vagrant reload    // 重启
vagrant destroy    // 销毁当前项目虚拟机
```

### 安装web服务器httpd

```
sudo yum install httpd  // 安装

sudo systemctl start httpd.service    // 启动httpd
systemctl status httpd.service        // 查看httpd状态

```

### 在Vagrantfile中配置同步目录

```
config.vm.synced_folder "[本地目录]", "[虚拟机对应目录]", create:[bool是否自动创建], owner:"[拥有者]", group:"[群组]"
vagrant reload    // 重启虚拟机
```

### 在Vagrantfile中配置网络

> ### 私有网络
>
> ```
> config.vm.network "private_network", ip: "192.168.33.10"
> vagrant reload        // 重启虚拟机
> ping 192.168.33.10    // 测试
> ```
>
> ### 共有网络
>
> ```
> config.vm.network "public_network"
> vagrant reload        // 重启虚拟机
> ssh登录后，ifconfig查看ip
> ping [ip]    // 测试
> ```



