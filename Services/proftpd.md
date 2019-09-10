### Install self-signed cert CentOS 7

- Create new files if file doesn't exists in `/etc/proftpd/tls.conf`

```
# Note that FTPS impose some limitations in NAT traversing.
# See http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html
# for more information.
#

<IfModule mod_tls.c>
TLSEngine                               on
TLSLog                                  /var/log/proftpd/tls.log
TLSProtocol                             TLSv1.2
TLSCipherSuite  

#
# Server SSL certificate. You can generate a self-signed certificate using 
# a command like:
#
# openssl req -x509 -newkey rsa:1024 \
#          -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt \
#          -nodes -days 365
#
# The proftpd.key file must be readable by root only. The other file can be
# readable by anyone.
#
# chmod 0600 /etc/ssl/private/proftpd.key 
# chmod 0640 /etc/ssl/private/proftpd.crt
# 
TLSRSACertificateFile                   /etc/proftpd/ssl/proftpd.crt
TLSRSACertificateKeyFile                /etc/proftpd/ssl/proftpd.key



# CA the server trusts...
#TLSCACertificateFile                    /etc/ssl/certs/CA.pem
# ...or avoid CA cert and be verbose
TLSOptions                      NoCertRequest AllowClientRenegotiations
# ... or the same with relaxed session use for some clients (e.g. FireFtp)
#TLSOptions                      NoCertRequest EnableDiags NoSessionReuseRequired
#
#
# Per default drop connection if client tries to start a renegotiate
# This is a fix for CVE-2009-3555 but could break some clients.
#
#TLSOptions                                                     AllowClientRenegotiations
#
# Authenticate clients that want to use FTP over TLS?
#
TLSVerifyClient                         off
#
# Are clients required to use FTP over TLS when talking to this server?
#
TLSRequired                             on
RequireValidShell                       no

#
# Allow SSL/TLS renegotiations when the client requests them, but
# do not force the renegotations.  Some clients do not support
# SSL/TLS renegotiations; when mod_tls forces a renegotiation, these
# clients will close the data connection, or there will be a timeout
# on an idle data connection.
#
#TLSRenegotiate                          required off
</IfModule>
```

- Create SSL Certificate Files for TLS

```
yum install openssl
```

- Gen SSL Cert by doing command. Make sure folder `/etc/proftpd/ssl` exists
```
openssl req -x509 -newkey rsa:1024 -keyout /etc/proftpd/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt -nodes -days 9999
```
It is local cert, Why bother expires? xD

- Change permission for thoses file to 600 for root have access only

```
chmod 600 /etc/proftpd/ssl/proftpd.*
```

- Don't forget restart service

```
systemctl restart proftpd
```

- Open Firewall to allow FTP over TLS Communication:
In order for clients to access ProFTPD and secure transfer files in Passive Mode you must open the entire port range between 1024 and 65534 on RHEL/CentOS Firewall, 
using the following commands.

```
firewall-cmd --add-port=1024-65534/tcp  
firewall-cmd --add-port=1024-65534/tcp --permanent
firewall-cmd --list-ports
firewall-cmd --list-services
firewall-cmd --reload
```

- In File Zilla client choose Require explicit FTP over TLS on Encryption and check the box that says Always trust certificate for future sessions and hit on OK

- If you have error something like 
```
425 Unable to build data connection: Operation not permitted
```

- Simple add new config in /etc/proftpd/proftpd.conf
```
TLSOptions NoSessionReuseRequired
```

- Then restart the service. Have fun!


### Gen password for proftpd

Scripts
```
#!/usr/bin/python

import crypt;

x = raw_input('Enter password: ')
print crypt.crypt(x, "$6$oZC3sKCq")
```
