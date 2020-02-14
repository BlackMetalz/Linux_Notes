-- For Wordpress backend use http, frontend haproxy use https
Add this into wp-config.php

```
$_SERVER['HTTPS']='on';
```
