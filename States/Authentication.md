## 2. Authentication

The authentication state's purpose is:

- The player identifying itself
- The server confirming the player's account
- The server sending back basic info about the player

### Purposes

```
0x06     Player public key
0x07     Auth ok
0x08     Auth failed
0x09     Player rejected
0x12     Start UDP
0x11     Ping (The server may kill the connection if a Ping is received before the client is authenticated)
```

### Formats

#### Player public key

Just the non-null-terminated string of the "public_key" field the backend sends on user login.

#### Auth failed

Non-null-terminated message detailing the reason for the failure.

#### Player rejected

Non-null-terminated message detailing the reason for the rejection, if any.

#### Auth ok

```
|       4       |
+---------------+
|   player_id   |
+---------------+
```

player_id: unsigned 4-byte little endian integer

#### Start UDP

```
|       8       |
+---------------+
|     magic     |
+---------------+
```

magic: 8-byte unsigned little endian integer. The value of `magic` shall be unique to the client, but not guessable.

Causes the client to establish a UDP connection and send the same packet back, at which point the magic is invalidated.

### Protocol

Only one of 7, 8, or 9 are valid responses to the public key. If it's not 7 (auth ok) the connection is terminated by the server.

```
C ----------------------------------------------------------- S
Player public key
                        Auth ok | Auth failed | Player rejected
                                                      Start UDP
```
