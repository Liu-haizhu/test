```js
#防火墙放行指定服务
firewall-cmd --add-service=ftp 
#查看所有已放行的端口
firewall-cmd --list=ports
#查看所有已放行的服务
firewall-cmd --list-services
#将指定tcp/udp端口放行
firewall-cmd --add-port=53/tcp

```
