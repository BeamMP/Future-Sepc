## ServerSessionSetup

### Purpose

```
0x0015  Players and vehicles info
0x0016  Ready
0xaa08  Change state to Playing
```

### Formats

#### Players and vehicles info

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
