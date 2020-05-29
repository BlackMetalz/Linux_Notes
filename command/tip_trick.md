# find log growth fast by watched it's size (credit: #hoangdh )
watch -n 1 "find /data/logs/ -cmin -1 -exec ls -l  {} \;"
