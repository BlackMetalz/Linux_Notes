- Input File: cut.txt
```
This is first line
this is second line
this is third line
```

- Get column 1 and 3:
```
kienlt@kienlt:~/Desktop$ cut -c 1,3 cut.txt 
Ti
ti
ti
```

- Get 4 letters first only:
```
kienlt@kienlt:~/Desktop$ cut -b -4 cut.txt 
This
this
this
```

- Get the word by delimiter ( space in this case )
```
kienlt@kienlt:~/Desktop$ cut -d' ' -f 2 cut.txt 
is
is
is
kienlt@kienlt:~/Desktop$ cut -d' ' -f 3 cut.txt 
first
second
third
```

