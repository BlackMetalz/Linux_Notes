- Find history usage with atop file, begin and end time

```
atop -r /var/log/atop/atop_20191104 -b 15:30 -e 15:50
```

we will have lots of useful information which caused overload CPU / MEM.
- For an example. This time server is full load of memory
```
MEM |  tot   125.8G |  free  361.5M |  cache 186.9M |  dirty   0.0M |  buff    3.3M  | slab  586.3M  |               |               |               |
```

and we have detailed what caused this

```
  PID  MEM COMMAND-LINE                                                                                                                          1/790
454665   9% python some/python/scripts.py
463963   4% python some/python/scripts.py
463959   4% python some/python/scripts.py
463962   4% python some/python/scripts.py
463961   4% python some/python/scripts.py
463956   4% python some/python/scripts.py
463964   4% python some/python/scripts.py
463965   4% python some/python/scripts.py
463958   4% python some/python/scripts.py
463960   4% python some/python/scripts.py
463957   4% python some/python/scripts.py
454667   4% python some/python/scripts.py
454671   4% python some/python/scripts.py
475411   3% python some/python/scripts.py
475388   3% python some/python/scripts.py
475389   3% python some/python/scripts.py
475410   3% python some/python/scripts.py
475398   3% python some/python/scripts.py
475409   3% python some/python/scripts.py
475387   3% python some/python/scripts.py
and so on
```
