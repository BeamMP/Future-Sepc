## 4. Session setup

### Purposes

```
0x000f    Players and vehicles info
0x0010    Ready
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
    "id": number,
    "role": string,
    "vehicles": [
      {
        "id": number,
        "data": { ... }, // game-internal json for the vehicle
        "status": { "pos": ..., "vel": ..., ... }, // latest position, rotation, etc. data
      },
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
