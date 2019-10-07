1. Check URL
One of the most common and simplest uses of cURL is typing the command itself, followed by the URL you want to check:
```
curl https://domain.com/
```

2. Save the output of the URL to a file

The output of a cURL command can be easily saved to a file by adding the -o option to the command, as shown below:
```
curl -o website https://domain.com/

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
Dload  Upload   Total   Spent    Left  Speed
100 41793    0 41793    0     0   275k      0 --:--:-- --:--:-- --:--:--  2.9M
```

In this example, the output will be saved to a file named ‘website’ in the current working directory. You can save in other directories using the same method as other programs by using forward-slashes.

3. Download files
You can download files with cURL by adding the -O option to the command. It is used for saving files on the local server with the same names as on the remote server:
```
curl -O https://domain.com/file.zip
```
In this example, the ‘file.zip’ zip archive will be downloaded to the current working directory.

You can also download the file with a different name by adding the -o option to cURL:

```
curl -o archive.zip https://domain.com/file.zip
```

This way the ‘file.zip’ archive will be downloaded and saved as ‘archive.zip’.

cURL can also be used to download multiple files simultaneously, as shown in the example below:

```
curl -O https://domain.com/file.zip -O https://domain.com/file2.zip
```
cURL can be also used to download files securely via SSH using the following command:

```
curl -u user sftp://server.domain.com/path/to/file
```

Note that you have to use the full path of the file you want to download.

4. Get HTTP header information from a website
You can easily get HTTP header information from any website you want by adding the -I option (capital ‘i’) to cURL.

```
curl -I http://domain.com

HTTP/1.1 200 OK
Date: Sun, 16 Oct 2016 23:37:15 GMT
Server: Apache/2.4.23 (Unix)
X-Powered-By: PHP/5.6.24
Connection: close
Content-Type: text/html; charset=UTF-8
```
5. Access an FTP server
To access your FTP server with cURL, use the following command:
```
curl ftp://ftp.domain.com --user username:password
```

cURL will connect to the FTP server and list all files and directories in the user’s home directory.

You can download files via FTP, too:

```
curl ftp://ftp.domain.com/filename.extension --user username:password
```
and upload a file onto the FTP server:

```
curl -T filename.extension ftp://ftp.domain.com/ --user username:password
```
You can also check the cURL manual page to see all available cURL options and functions:

Credit: https://www.rosehosting.com/blog/curl-command-examples/


6. CURL with header:

```
curl -I -H "key:value" https://domain.com/abc/xyz
```

7. CURL with basic auth:
```
curl --user daniel:secret http://example.com/
```

