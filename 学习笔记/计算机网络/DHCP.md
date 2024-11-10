# cisco配置dhcp
```js
#创建地址池
Switch(config)#ip dhcp pool vlan10
#配置下发IP地址范围
Switch(dhcp-config)#network 192.168.10.0 255.255.255.0
#配置网关
Switch(dhcp-config)#default-router 192.168.10.254
#配置DNS
Switch(dhcp-config)#dns-server 10.1.1.3
#配置排除地址
Switch(config)#ip dhcp excluded-address 192.168.10.252 192.168.10.254

```