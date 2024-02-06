## QuickJoin

### Purposes

```
0x0007  DoJoin
0x0008  JoinOk
0x0009  JoinDeny
0xaa03  State change to Browsing
0xaa04  State change to ServerIdentification
```

### Formats

#### DoJoin

```json5
{
  "host": string,
  "port": number,
}
```

### Protocol

#### Case 1: Join
```
L -------------------------------- G
DoJoin
                              JoinOK
State change to ServerIdentification
```


#### Case 2: Join + deny
```
L -------------------------------- G
DoJoin
                            JoinDeny
State change to Browsing
```

#### Case 3: Nothing to join
```
L -------------------------------- G
State change to Browsing
```
