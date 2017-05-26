#### 指令

```
su [username]         // 切换用户
useradd [username]    // 添加用户，默认会添加同名的用户组（root）
passwd [username]     // 设置用户的登录密码（root）
userdel [username] -r // 删除用户（root）,-r表示同时删除用户目录
```

#### 使用户可获得sudo执行权限

```
// 方式1：将用户添加至wheel群组中
sudo gpasswd -a zhangsan wheel   // 查看群组下的用户：sudo lid -g wheel
// 方式2：添加用户同名文件夹至 /etc/sudoers.d文件夹下
```

#### 文件和文件夹权限

> ##### u=用户g=群组o=其他
>
> ##### r=4,w=2,x=1

> #### 修改权限
>
> ```
> chmod xxx  [file_path]    // 修改文件权限
> chmod o+r  [file_path]    // 为其他人添加读取权限
> chmod g+x  [file_path]    // 为群组添加执行权限
> chmod u-w  [file_path]    // 为用户去除写入权限
> chmod -R xxx  [dir_path]  // 修改文件夹权限 ，-R表示递归修改
> chown -R leon:leon [dir_path]  // 修改文件夹的所属用户和用户组
> ```

```
touch files/file_{01..10}.txt    // 在files目录下创建是个文件
```



