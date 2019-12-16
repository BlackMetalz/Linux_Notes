## Credit: https://www.itechlounge.net/2015/05/linux-how-to-tune-up-receive-tx-and-transmit-rx-buffers-on-network-interface/

- Get information about rx errors:

```
root@XXXX:~# ethtool -S eno1 | grep errors
     rx_crc_errors: 132
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_window_errors: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
     rx_align_errors: 0
     rx_errors: 264
     tx_errors: 0
     rx_length_errors: 0
     rx_over_errors: 0
     rx_frame_errors: 0
     rx_fifo_errors: 356
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
```

See `rx_fifo_errors: 356`? 

- Get current ring parameters for eno1
```
root@XXXX:~# ethtool -g eno1
Ring parameters for eno1:
Pre-set maximums:
RX:             4096
RX Mini:        0
RX Jumbo:       0
TX:             4096
Current hardware settings:
RX:             256
RX Mini:        0
RX Jumbo:       0
TX:             256
```

- Change it:
```
root@XXXX:~# ethtool -G eno1 rx 4096
```

# It doesn't work, just a practice :))
