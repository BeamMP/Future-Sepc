## ClientIdentification

### Purposes

```
0x0001  Game info
0x0002  Launcher info
0x0003  Error
0xaa01  State change to Login
```

### Formats

#### Game Info

```json5
{
  "implementation": string,
  "mod_version": [major, minor, patch],
  "game_version": [major, minor, patch],
  "protocol_version": [major, minor, patch]
}
```

#### Launcher Info

```json5
{
  "implementation": string,
  "version": [major, minor, patch],
  // path to the launcher's mod cache
  "mod_cache_path": string,
}
```

#### Error

```json5
{
  "message": string,
}
```

### Protocol

```
L -------------------------------- G
launcher info
                           game info
state change to login
```
