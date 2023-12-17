
```
|  8  |  16  |  24   |  32  |  40  |  48  |  56  |  64  |
+-----+------+-------+------+------+------+------+------+
|   purpose  | flags |  RSV |            size           |
+------------+-------+------+---------------------------+
|                           ...                         |
|                          body                         |
|                           ...                         |
+                                                       +
```

- Purpose: 3 byte, enum, 4 bytes little endian with the last byte cut off)
- Flags: 1 byte
- RSV: 1 byte, Reserved for future use
- Size: 4 bytes, unsigned integer, little endian

Reserved (RSV) fields may be any value, and the value of these fields MUST be ignored.

## Purpose

The purpose specifies the purpose of the data, regardless of the way it's transmitted. For example, the purpose would specify "this is water", not which form it comes in (bottled, frozen, etc.) as that would be the job of the [flags](#flags).

## Flags

```
|    7    |    6    |    5    |    4    |    3    |    2    |    1    |    0    |
+---------+---------+---------+---------+---------+---------+---------+---------+
|   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   comp  |
```

- Comp: Compressed (zstd)
