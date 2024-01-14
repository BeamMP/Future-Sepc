## 4. Session setup

### Purposes

```
15    Players and vehicles info
16    Ready
```

The ready packet is sent by the launcher once all players and vehicles are processed (spawned, for example).

### Formats

#### Players info

json:

```json5
[
  {
    // player name
    "name": string,
    // server id
    "id": string,
    "role": string,
    "vehicles": [
      { ... }, // game-internal json for the vehicle
      ...
    ]
  },
  ...
]
```

### Protocol

```
C --------------------------------------- S
                  players and vehicles info
Ready
```
