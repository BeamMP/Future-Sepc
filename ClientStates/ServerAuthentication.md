## ServerAuthentication

### Purposes

```
0x000f  AuthenticationError
0x0010  AuthenticationOk
0x0011  PlayerRejected
0xaa06  State change to ServerModDownload
```

### Formats

#### AuthenticationError, PlayerRejected

```json5
{
  "message": string,
}
```

#### AuthenticationOk

```json5
{
  "pid": number,
}
```
