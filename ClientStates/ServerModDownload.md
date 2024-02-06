## ServerAuthentication

### Purposes

```
0x0012  ModSyncStatus
0x0013  MapInfo
0xaa07  State change to ServerSessionSetup
```

### Formats

#### ModSyncStatus

```json5
[
  {
    // name of the mod file, e.g. 'ks_spa.zip'
    "name": string,
    // hash of the mod file
    "hash": string,
    // algorithm used for the hash
    "hash_algorithm": string,
    // where to get the mod from (direct = from the server)
    "location": {
      "protocol": "direct",
    },
    // size of the mod in bytes
    "size": 12345,
    // whether this mod is optional
    "optional": false,
    // remaining bytes
    "remaining": number,
    // download speed in B/s
    "speed": number
  },
  ...
]
```

#### MapInfo

```json5
{
  // e.g. /levels/west_coast_usa/info.json
  "map": string,
}
```
