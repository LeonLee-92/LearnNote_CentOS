#### 概念

> #### 默认有三个chain：INPUT, OUTPUT, FORWARD
>
> #### rules 规则
>
> #### policy  默认动作
>
> #### target 动作
>
> > ##### Accept通过
> >
> > ##### Drop丢弃
> >
> > ##### Reject 拒绝

#### 命令

> ##### // 查看chain和chain下的rules
>
> #### sudo iptables -L --line-numbers
>
> ##### // 查看INPUT这个chain下的rules
>
> #### sudo iptables -L INPUT --line-numbers
>
> ##### // 查看INPUT这个chain下的rules，并显示统计流量
>
> #### sudo iptables -L INPUT --line-numbers  -v
>
> ##### // 对防火墙统计流量清零
>
> #### sudo iptables -Z
>
> ##### // 查看chain的policy和chain下rules的动作
>
> #### sudo iptables --list-rules
>
> ##### // 查看现有防火墙policy
>
> #### sudo iptables -S
>
> ##### // 改变chain的policy
>
> #### sudo iptables -P 【chain】 【policy】
>
> ##### // 在某chain下追加rule
>
> #### sudo iptables -A 【chain】 -s 【来源ip】 -j  【动作target】
>
> ##### // 添加某网段规则
>
> #### sudo iptables -A 【chain】 -s 192.168.33.0/24  -j  【动作target】
>
> ##### //用例：在INPUT这个chain下追加规则，对192.168.33.xxx网段禁止使用tcp协议在80端口访问
>
> #### sudo iptables -A INPUT -s 192.168.33.0/24 -p tcp --dport 80  -j  DROP
>
> ##### //用例：插入到具体位置
>
> #### sudo iptables -I INPUT  2  -s 192.168.33.0/24 -p tcp --dport 80  -j  DROP
>
> ##### // 删除INPUT下的第2条rule
>
> #### sudo iptables -D  INPUT  2
>
> ##### // 删除INPUT下所有规则
>
> #### sudo iptables -F INPUT 
>
> ##### // 删除所有chain下的所有规则
>
> #### sudo iptables -F

#### 

#### 安装iptables-services用于使现有的规则持久化

> 1. 安装sudo yun install iptables
> 2. 启动sudo systemctl start iptables
> 3. 开机自启动sudo systemctl enable iptables
> 4. 服务将规则存储在 /etc/sysconfig/iptables
> 5. 重启 sudo systemctl reload iptables
> 6. 每次修改过过iptables规则后都要保存一下 sudo service iptables save

#### 将INPUT的policy改为DROP，初始化数据库

> 1. 删除现有的所有规则
> 2. sudo iptables -F
> 3. 保存设置
> 4. sudo service iptables save
> 5. 为现有操作和连接添加白名单
> 6. sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
> 7. 设置ssh白名单
> 8. sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
> 9. 最后将INPUT的policy改为DROP
> 10. sudo iptables -P INPUT DROP
> 11. 保存设置
> 12. sudo service iptables save
> 13. 设置本地流量白名单
> 14. sudo iptables -I INPUT 1 -i lo -j ACCEPT
> 15. 设置web服务白名\
> 16. sudo iptables -A INPUT  -p tcp --dport 80 -j ACCEPT
> 17. sudo iptables -A INPUT  -p tcp --dport 443 -j ACCEPT
> 18. 保存设置
> 19. sudo service iptables save



