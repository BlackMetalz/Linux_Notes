# Create custom service in Centos / Ubuntu using systemd
- Create service file
```
touch /etc/systemd/system/your-service.service
```

- Edit it with following information:
Note: 
+ You can change root to specific user with /sbin/nologin for security or something like that
+ Path of python3 must be absolute!
```
[Unit]
Description=Your Service
After=network.target

[Service]
Type=simple
User=root 
ExecStart=/bin/python3 /data/tool_checkmk/tool_checkmk.py
Restart=on-abort


[Install]
WantedBy=multi-user.target
```

- After that reload to get new service
```
systemctl daemon-reload
```

- Enable and start it:
```
systemctl enable your-service
systemctl start your-service
```

- Check status
```
systemctl status your-service
```


More details go here: https://www.opentechguides.com/how-to/article/centos/169/systemd-custom-service.html or gooogle
