#### 添加仓库：

```
yum repolist       查看启用的仓库
yum search [repo]  查找仓库
yum install epel-release -y  添加epel仓库
yum install https://centos7.iuscommunity.org/ius-release.rpm -y  添加ius仓库
```

#### 指令：

```
yum search [name]             搜索
yum info [name]               包的详情    
yum install [name]            安装
yum check-update  [name]      检查更新
yum update/upgrade [name]     升级
yum installed | grep [...]    查看安装过的包
yum remove [name]             删除
```



