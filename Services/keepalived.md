# What is keepalived:

Keepalived is used for IP failover between two servers. Its facilities for load balancing and high-availability to Linux-based infrastructures. It worked on VRRP (Virtual Router Redundancy Protocol) protocol. In this tutorial, we have configured IP failover between two Linux systems running as a load balancer for load balancing and high-availability infrastructures.



1. Install in ubuntu 18-20
```
apt install keepalived -y
```

1.1 Require 2 servers ++

2. Config: create new file with info below /etc/keepalived/keepalived.conf
```
vrrp_instance VIP_92_215 {
    state MASTER #  Change this to BACKUP on second/third...
    interface eth0 # interface 
    virtual_router_id 101 #  This should be same
    priority 100 # 100 for master, 90 for the first backup and 80 for second backup. Something like that xD
    advert_int 1 # specify the advertisement interval in seconds. Recommend seem like alway: 1
    authentication { # authen..
        auth_type PASS
        auth_pass asdasd
    }
    virtual_ipaddress { # By default single vrrp_instance support up to 20 virtual_ipaddress. In order to add more addresses you need to add more vrrp_instance
        10.5.92.215 # your virtual IP
    }
}

```

Read more here:
https://tecadmin.net/setup-ip-failover-on-ubuntu-with-keepalived/
https://keepalived.readthedocs.io/en/latest/configuration_synopsis.html
