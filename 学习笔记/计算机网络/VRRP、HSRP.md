# cisco配置hsrp
```js
#进入vlan接口
Switch(config)#int vlan 10
#创建组10虚拟网关IP
Switch(config-if)#standby 10 ip 192.168.10.254
#设置网关主从配置优先级，默认100
Switch(config-if)#standby 10 priority 150
#开启抢占功能，否则在配置从网关的时候不会选举出主备
Switch(config-if)#standby preempt

```