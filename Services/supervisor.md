- Put it in config folder of supervisor
```
[program:your-program-name]
directory=/data/wtf
user=custom_user_or_root
group=custom_user_or_root
autostart=true
autorestart=true
command=node /data/wtf/cron_job.js
stderr_logfile = /var/log/supervisor/your-program-name_cronjob-stderr.log
stdout_logfile = /var/log/supervisor/your-program-name_cronjob-stdout.log
```
