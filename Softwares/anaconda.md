-- Credit:
https://docs.anaconda.com/anaconda/install/linux/
https://docs.anaconda.com/anaconda/install/multi-user/

1. Download anaconda from this page: `https://www.anaconda.com/download/#linux`
```
wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
chmod +x Anaconda3-2019.10-Linux-x86_64.sh
bash Anaconda3-2019.10-Linux-x86_64.sh

```
2. Run script for install and set path like /data/anaconda3 ( for multiple user uses later )

3. Add new group called anaconda3 or anaconda depend what version u installed
```
groupadd anaconda3
# Change /data/anaconda3
chown root:anaconda3 /data/anaconda3
chmod 770 /data/anaconda3
usermod -a -G anaconda3 your_user
```



