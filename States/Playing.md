## 5. Playing

### Purposes

```
0x0011    Ping
0x0101    Vehicle spawn (Os)
0x0102    Vehicle delete (Od)
0x0103    Vehicle reset (Or)
0x0104    Vehicle edited (Oc)
0x0105    Vehicle coupler changed (Om)
0x0106    Spectator switched (Ot)
0x0201    Apply input (Vi)
0x0301    Apply electrics (We)
0x0401    Apply nodes (Xn)
0x0402    Apply breakgroups (Xg)
0x0501    Apply powertrain (Yl)
0x0601    Apply position (Zp)
0x0701    Chat message (C)
0x0801    Event (E)
0x0901    Player joined (J)
0x0902    Player left
0x0903    Player ping updated
0x0a01    Notification (L)
0x0b01    Kicked (K)
```

### Formats

```
|     4    |   2   |  ...
+----------+-------+-------
|    pid   |  vid  |  data
+----------+-------+-------
```

Invalid/null pid: 0xffffffff
Invalid/null vid: 0xffff

#### 0x0101-0x0601

Json body

#### Chat message

Not-null-terminated message string

#### Event

json:
```json5
{
  // event name
  "name": string,
  // arbitrary event arguments
  "args": [ ... ]
}
```

#### Player joined

json:
```json5
{
  "name": string,
  "role": string
}
```

