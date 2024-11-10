# Cisco配置port-channel
```js
#创建聚合组1
Switch(config)#interface port-channel 1 
#进入物理端口
Switch(config)#interface range g1/0/4-5
#设置trunk封装协议为dot1q
Switch(config-if-range)#switchport trunk encapsulation dot1q
#设置端口模式并放行vlan
Switch(config-if-range)#switchport mode trunk
#加入聚合组1，并设置模式为on
Switch(config-if-range)#channel-group 1 mode on








```