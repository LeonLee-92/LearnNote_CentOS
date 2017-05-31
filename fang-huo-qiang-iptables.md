#### 概念

默认有三个chain：INPUT, OUTPUT, FORWARD

rules 规则

policy  默认动作

target 动作

Accept通过

Drop丢弃

Reject 拒绝





#### 命令

sudo iptables -L --line-numbers  查看chain和chain下的rules

sudo iptables -L INPUT --line-numbers   查看INPUT这个chain下的rules

sudo iptables -L INPUT --line-numbers  -v  查看INPUT这个chain下的rules，并显示统计流量

sudo iptables -Z  对防火墙统计流量清零

sudo iptables --list-rules    查看chain的policy和chain下rules的动作

sudo iptables -S  查看现有防火墙policy  （-L  =  --list-rules）

sudo iptables -P 【chain】 【policy】   改变chain的policy

sudo iptables -A 【chain】 -s 【来源ip】 -j  【动作target】   // 在某chain下追加rule

sudo iptables -A 【chain】 -s 192.168.33.0/24  -j  【动作target】   // 添加某网段规则

//用例：在INPUT这个chain下追加规则，对192.168.33.xxx网段禁止使用tcp协议在80端口访问

sudo iptables -A INPUT -s 192.168.33.0/24 -p tcp --dport 80  -j  DROP

//用例：插入到具体位置，将-A换为-I

sudo iptables -I INPUT  2  -s 192.168.33.0/24 -p tcp --dport 80  -j  DROP

// 删除INPUT下的第2条rule

sudo iptables -D  INPUT  2

// 删除INPUT下所有规则

sudo iptables -F INPUT  
// 删除所有chain下的所有规则

sudo iptables -F



#### 将INPUT的policy改为DROP，初始化数据库

删除现有的所有规则

sudo iptables -F  

保存设置

sudo service iptables save 

为现有操作和连接添加白名单

sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

设置ssh白名单

sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

最后将INPUT的policy改为DROP

sudo iptables -P INPUT DROP

保存设置

sudo service iptables save 

设置本地流量白名单

sudo iptables -I INPUT 1 -i lo -j ACCEPT

设置web服务白名\

sudo iptables -A INPUT  -p tcp --dport 80 -j ACCEPT

sudo iptables -A INPUT  -p tcp --dport 443 -j ACCEPT

保存设置

sudo service iptables save 





#### 安装iptables-services用于使现有的规则持久化

安装sudo yun install iptables

启动sudo systemctl start iptables

开机自启动sudo systemctl enable iptables

服务将规则存储在 /etc/sysconfig/iptables

重启 sudo systemctl reload iptables

每次修改过过iptables规则后都要保存一下

sudo service iptables save

