- Mount remote directory from command:
```
sshfs recsysnews@10.5.0.222:/data/recsysnews /data/recsysnews/ -o port=2395,identityfile=/home/recsysnews/.ssh/id_rsa,uid=1017,gid=1017,allow_other
```

+ port is custom port for ssh if you dont use default 22
+ identityfile : ssh key
+ -o uid: set file owner
+ -o gid: set file group
+ -o allow_other: allow access to other users

ofc need ssh key already setup.  and UID & GUID should be some as in 10.5.0.222

- In fstab for auto mount when server startup, insert in rc.local
Duo this mount related to network, so we can avoid error if we use mount by /etc/fstab
