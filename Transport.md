
```
|  8  |  16  |  24  |  32   |  40  |  48  |  56  |  64  |
+-------------------+-------+------+------+------+------+
|    type    |  RES | flags |            size           |
+-------------------+-------+---------------------------+
|                           ...                         |
|                          body                         |
|                           ...                         |
+                                                       +
```

- Type: 3 byte, enum
- RES: 1 byte, Reserved for future use
- Flags: 1 byte
- Size: 4 bytes, unsigned integer
