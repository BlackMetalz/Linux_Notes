- Add route for network 

```
ip route add 10.3.48.0/22 via 172.17.4.1 dev vlan704
route -n
```

- hmmm

```
ip route add 192.168.1.0/24 via 10.5.0.1
```

10.5.0.1 is gateway
192.168.1.0/24 is ip destination
