- Mount:
```
/data/docker-compose/somesite/cronjob/www-data:/var/spool/cron/crontabs/www-data
```
- Permission: 
```
chown root:root /data/docker-compose/somesite/cronjob/www-data && chmod 600 /data/docker-compose/somesite/cronjob/www-data
```
