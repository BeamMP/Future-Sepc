## 2. Authentication

The authentication state's purpose is:

- The player identifying itself
- The server confirming the player's account
- The server sending back basic info about the player

### Purposes

```
6    Player public key
7    Auth ok
8    Auth failed
9    Player rejected
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

### Protocol

Only one of 7, 8, or 9 are valid responses to the public key. If it's not 7 (auth ok) the connection is terminated by the server.

```
C ----------------------------------------------------------- S
Player public key
                        Auth ok | Auth failed | Player rejected
```
