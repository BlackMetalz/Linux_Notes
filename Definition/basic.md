A common mistake is that ctime is the file creation time. This is not correct, it is the inode/file change time. 
mtime is the file modification time. A often heard question is "What is the ctime, mtime and atime?". 
This is confusing so let me explain the difference between ctime, mtime and atime.

ctime
ctime is the inode or file change time. The ctime gets updated when the file attributes are changed, 
like changing the owner, changing the permission or moving the file to an other filesystem but will also be updated 
when you modify a file.

mtime
mtime is the file modify time. The mtime gets updated when you modify a file. Whenever you update content of a file or save a 
file the mtime gets updated.
Most of the times ctime and mtime will be the same, unless only the file attributes are updated. 
In that case only the ctime gets updated.

atime
atime is the file access time. The atime gets updated when you open a file but also when a file is used for other 
operations like grep, sort, cat, head, tail and so on.




-- Credit: https://www.quora.com/What-is-the-difference-between-mtime-atime-and-ctime
