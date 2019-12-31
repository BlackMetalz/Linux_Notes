-- Credit:
https://docs.anaconda.com/anaconda/install/linux/
https://docs.anaconda.com/anaconda/install/multi-user/

1. Download anaconda from this page: `https://www.anaconda.com/download/#linux`

2. Run script for install and set path like /data/anaconda3 ( for multiple user uses later )

3. Add new group called anaconda3 or anaconda depend what version u installed
```
groupadd anaconda3
# Change /data/anaconda3
chown root:anaconda3 /data/anaconda3
chmod 770 /data/anaconda3
usermod -a -G anaconda3 your_user
```



