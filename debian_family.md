- Install package without confirm and keep old config file: 

```
apt-get install -o Dpkg::Options::="--force-confold" --force-yes -y ntp
```


More information: 
https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/
