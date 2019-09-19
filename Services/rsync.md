- Rsync with custom port

```
rsync -azu -e 'ssh -p 2395' www-data@99.99.99.99:/data/web /data/ --delete
```

- Rsync with exclude single file
```
rsync -azu --exclude=file.txt 
```

- Rsync with multiple file and folder exclude
```
rsync -azu --exclude={'file1.txt','folder1'}
```
