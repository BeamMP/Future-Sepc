## 3. Mod Download

The mod download state handles syncing of mods needed to join the server (e.g. maps).

The server can specify how the client must download the mods present.

### Purposes

```
0x000a   Mods info
0x000b   Mod request
0x000c   Mod response
0x000d   Mod request invalid
0x000e   Mods sync done
0x0013   Map info
0x0011   Ping
```

### Format

#### Mods info

The server mods info packet specifies:

- The name of the mod
- The hash of the mod
- The hash algorithm
- Where to get the mod
- Mod size
- Whether the mod is optional

json:

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
  },
  ...
]
```

Supported `hash_algorithm` values:

- `sha256`

#### Mod request

String of the format (not null-terminated):

```
<hash algorithm>:<hash>
```

#### Mod response

String of the format (not null-terminated):

```
<hash algorithm>:<hash>
```

Followed immediately by the mod file's bytes (binary).

#### Mod request invalid

String (not null-terminated) detailing the reason for the failure.

#### Map info

String (not null-terminated) specifying the map path (e.g. `/levels/east_coast_usa/info.json`).

### Protocol

```
C --------------------------------------- S
                                  mods info
mod request(s)
...                  mod request invalid (?)
Mods sync done
```

Transfer into next state: Session setup
