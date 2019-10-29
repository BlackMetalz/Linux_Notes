- Install Tool iperf3:
```
apt install iperf3 or yum install iperf3
```
- What is iperf3 ( copy from google )

```
iperf  is a free and open source cross-platform command-line tool used for checking network performance in terms 
of bandwidth and speed. It is a highly reliable tool in comparison to the many network bandwidth and speed testing tools. 
In addition, it is a highly effective tool when testing for network performance between 2 servers spread across different 
geographical regions.
```

1. How to start
- Instal iperf3 in both server we want to test
- Example we have 2 server A and B:
in Server A do this command To set an iperf3 server:

```
iperf3 -s
```

Output:

```
root@kienlt-lab-48:~# iperf3 -s
-----------------------------------------------------------
Server listening on 5201
```

in server B do this command to Connecting Client to server:
```
iperf3 -c server_a_Ip
```

Output:
```
root@kienlt-lab-48:~# iperf3 -c 10.3.48.56 -t 100 -i 1
Connecting to host 10.3.48.56, port 5201
[  4] local 10.3.48.82 port 42124 connected to 10.3.48.56 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   709 MBytes  5.95 Gbits/sec  1357   2.17 MBytes
[  4]   1.00-2.00   sec   732 MBytes  6.14 Gbits/sec  1648   1.77 MBytes
[  4]   2.00-3.00   sec   768 MBytes  6.44 Gbits/sec  701   1.20 MBytes
[  4]   3.00-4.00   sec   799 MBytes  6.70 Gbits/sec  249   1.03 MBytes
[  4]   4.00-5.00   sec   786 MBytes  6.59 Gbits/sec    5   1.06 MBytes
[  4]   5.00-6.00   sec   816 MBytes  6.85 Gbits/sec   12   1.12 MBytes
[  4]   6.00-7.00   sec   756 MBytes  6.34 Gbits/sec  408   1.12 MBytes
[  4]   7.00-8.00   sec   775 MBytes  6.50 Gbits/sec  541    881 KBytes
[  4]   8.00-9.00   sec   801 MBytes  6.72 Gbits/sec    0   1.35 MBytes
[  4]   9.00-10.00  sec   759 MBytes  6.37 Gbits/sec  439    996 KBytes
[  4]  10.00-11.00  sec   684 MBytes  5.73 Gbits/sec  248    990 KBytes
[  4]  11.00-12.00  sec   819 MBytes  6.87 Gbits/sec  206   1.19 MBytes
[  4]  12.00-13.00  sec   791 MBytes  6.64 Gbits/sec  347   1.33 MBytes
[  4]  13.00-14.00  sec   810 MBytes  6.79 Gbits/sec  452   1.15 MBytes
[  4]  14.00-15.00  sec   811 MBytes  6.80 Gbits/sec  387    956 KBytes
[  4]  15.00-16.00  sec   808 MBytes  6.78 Gbits/sec    0   1.44 MBytes
[  4]  16.00-17.00  sec   778 MBytes  6.52 Gbits/sec  331   1.02 MBytes
[  4]  17.00-18.00  sec   732 MBytes  6.14 Gbits/sec  261   1.43 MBytes
[  4]  18.00-19.00  sec   784 MBytes  6.57 Gbits/sec  663    946 KBytes
[  4]  19.00-20.00  sec   781 MBytes  6.55 Gbits/sec  201   1.23 MBytes
[  4]  20.00-21.00  sec   848 MBytes  7.11 Gbits/sec  175   1.33 MBytes
```

More detail please read in man page of iperf3 :)
