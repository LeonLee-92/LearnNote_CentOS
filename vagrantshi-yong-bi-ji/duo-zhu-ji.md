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
// config.vm.network "public_network"
// 或
// config.vm.network "private_network", ip: "192.168.xx.xx"
vagrant reload // 启动
ifconfig // 查看ip
// 互ping测试
```



