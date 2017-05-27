##### 端口扫描工具nmap

> 1.使用yum install nmap安装nmap
>
> 2.nmap -sT  \[目标ip\]  扫描端口   （-sT   s表示scan扫描，T表示TCP协议）

##### 列出系统使用的端口和对应服务

> sudo cat /etc/services \| grep xxx

##### 查看指定端口是谁打开的

> sudo  netstat  -anp  \|  grep \[prot\]   // 检索所有协议
>
> sudo  netstat  -ntp  \|  grep \[prot\]   // 只检索tcp协议





