## Client Transport

```
|    1    |       2       |     4     |    2    |      4      |   ...  
+---------+---------------+-----------+---------+-------------+-------
|  target |    purpose    |    pid    |   vid   |     size    |  data
+---------+---------------+-----------+---------+-------------+-------
```

- `target`: `C` for launcher-to-game communication, `G` for game-to-server communication.
- `purpose`: The type of packet / purpose of this packet.
- `pid`: Player ID, `0xffffffffffffffff` = "not a pid".
- `vid`: Vehicle ID, `0xffffffff` = "not a vid".
- `size`: Size of `data`.
- `data`: Binary data.
