-- Install package without confirm and keep old config file: 

```
apt-get install -o Dpkg::Options::="--force-confold" --force-yes -y ntp
```

-- Remove hold package:
- List hold packge: `dpkg --get-selections | grep hold`
- Remove hold ` echo "package_name install" | dpkg --set-selections `

More information: 
https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/
