- Rsync with custom port and delete files has been removed from source folder

```
rsync -azu -e 'ssh -p 2395' www-data@99.99.99.99:/data/web /data/ --delete
```

- Rsync with exclude single file
```
rsync -aqx --exclude=file.txt   # rsync windows
rsync -aqx --exclude 'file.txt' #Linux
```

- Rsync with multiple file and folder exclude
```
rsync -aqx --exclude={'file1.txt','folder1'}  # rsync windows
rsync -aqx --exclude 'file1.txt','folder1'  # rsync linux. Not test :D
```

- Rsync docker
```
rsync -aqxP /var/lib/docker/ /data1/docker
```
