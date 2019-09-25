- Mount remote directory from command:
```
sshfs recsysnews@10.3.68.65:/data/recsysnews /data/recsysnews/ -o port=2395,identityfile=/home/recsysnews/.ssh/id_rsa,uid=1017,gid=1017
```

ofc need ssh key already setup. 

- In fstab for auto mount when server startup, insert in rc.local
