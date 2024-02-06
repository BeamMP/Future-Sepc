## ClientIdentification

### Purposes

```
0x0004  AskForCredentials
0x0005  Credentials
0x0006  LoginResult
0xaa02  State change to QuickJoin
```

### Formats

#### AskForCredentials

Empty body.

#### Credentials

```json5
{
  "username": string,
  "password": string,
}
```

#### LoginResult

```json5
{
  "success": true | false,
  "message": string,
}
```

#### Error

```json5
{
  "message": string,
}
```

### Protocol

#### Already logged in

```
L -------------------------------- G
LoginStatus
State change to QuickJoin
```
