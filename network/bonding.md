Credit: https://www.nextstep4it.com/check-network-bonding-in-centos-rhel/
- Get bonding interface
```
[root@VAAA ~]# ifconfig | grep -i bond
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
```

- Show information about bonding status:
```
[root@VAAA ~]# cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer3+4 (1)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: fast
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: 00:25:90:85:81:f2
Active Aggregator Info:
	Aggregator ID: 2
	Number of ports: 1
	Actor Key: 9
	Partner Key: 1
	Partner Mac Address: 00:00:00:00:00:00

Slave Interface: enp1s0f0
MII Status: down
Speed: Unknown
Duplex: Unknown
Link Failure Count: 2
Permanent HW addr: 00:25:90:85:81:f2
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: churned
Partner Churn State: churned
Actor Churned Count: 1
Partner Churned Count: 2
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:25:90:85:81:f2
    port key: 0
    port priority: 255
    port number: 1
    port state: 71
details partner lacp pdu:
    system priority: 65535
    system mac address: 00:00:00:00:00:00
    oper key: 1
    port priority: 255
    port number: 1
    port state: 1

Slave Interface: enp1s0f1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 2
Permanent HW addr: 00:25:90:85:81:f3
Slave queue ID: 0
Aggregator ID: 2
Actor Churn State: none
Partner Churn State: churned
Actor Churned Count: 1
Partner Churned Count: 3
details actor lacp pdu:
    system priority: 65535
    system mac address: 00:25:90:85:81:f2
    port key: 9
    port priority: 255
    port number: 2
    port state: 79
details partner lacp pdu:
    system priority: 65535
    system mac address: 00:00:00:00:00:00
    oper key: 1
    port priority: 255
    port number: 1
    port state: 1
[root@VAAA ~]# 
````
