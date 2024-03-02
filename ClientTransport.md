## Client Transport

```
|    1    |       2       |     4     |    2    |      4      |   ...  
+---------+---------------+-----------+---------+-------------+-------
|  flags  |    purpose    |    pid    |   vid   |     size    |  data
+---------+---------------+-----------+---------+-------------+-------
```

- `flags`: See [flags](#flags).
- `purpose`: The type of packet / purpose of this packet.
- `pid`: Player ID, `0xffffffffffffffff` = "not a pid".
- `vid`: Vehicle ID, `0xffffffff` = "not a vid".
- `size`: Size of `data`.
- `data`: Binary data.

### Flags

```
|    7    |    6    |    5    |    4    |    3    |    2    |    1    |     0      |
+---------+---------+---------+---------+---------+---------+---------+------------+
|   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   RSV   |   msgpack  |
```
