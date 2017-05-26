##### vagrant init \[centos/7\]

### 基本配置

> ![](/assets/imsdfport.png)
>
> #### 启动单个主机
>
> ```
> vagrant up development
> vagrant status
>
> --> Current machine states:
>
>     development               running (virtualbox)
>     production                running (virtualbox)
> ```
>
> #### 启动全部定义主机
>
> ```
> vagrant up    
> vagrant status
>
> --> Current machine states:
>
>     development               running (virtualbox)
>     production                poweroff (virtualbox)
> ```

### 登录主机

```
vagrant ssh [development]
```

### 在config.vm.define中配置网络

```
// [HostName].vm.network "public_network"
// 或
// [HostName].vm.network "private_network", ip: "192.168.xx.xx"
vagrant reload // 启动
ifconfig // 查看ip
// 互ping测试
```

### 修改主机名

```
// [HostName].vm.hostname = "[name]"  // --> vagrant reload 
// 或
// 修改 /etc/sysconfig/network 文件    // --> systemctl reload network.service
```

### 分别设置共享目录

#### 注意：只在虚拟机启动时同步一次

```
// [HostName].vm.synced_folder = "本机地址","虚拟机地址"  // --> vagrant reload 

// 例如：将当前目录下的development文件夹与虚拟机根目录下的vagrant文件夹同步
// [HostName].vm.synced_folder "development","/vagrant"
```



