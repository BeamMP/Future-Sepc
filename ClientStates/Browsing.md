## Browsing

### Purposes

```
0x000a  ServerListRequest
0x000b  ServerListResponse
0x0003  Error
0x000c  Connect
0x000d  Logout
???     RequestServerInfo // TODO
0xaa04  State change to ServerIdentification
```

### Formats

#### ServerListResponse

Server list json.

#### Connect

```json5
{
  "host": string,
  "port": number,
}
```
