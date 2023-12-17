## 1. Identification

The identification state's purpose is:

- The client informing the server of program version, protocol version, game version, mod version and implementation (more info on this further down)
- The server informing the client of program version, confirming/denying support for the protocol, game and mod versions, and informing of implementation

### Formats

#### Versions

Each version is represented by 12 bytes, binary, unsigned, little endian, as follows:

```
|    2    |    4    |    6    |    8    |    10   |    12   |
+---------+---------+---------+---------+---------+---------+
|      major        |       minor       |       patch       |
+-------------------+-------------------+-------------------+
```

#### Implementation

An ASCII string of at most 255 characters, prefixed by the length in one byte, **not** null-terminated.

```
|    1    |  2...   |
+---------+---------+
|   size  |   ...   |
+---------+---------+
```

### Purposes

```
 1          Protocol version
 2          Protocol version ok
 3          Protocol version bad
 4          Client info
 5          Server info
```

### Protocol

```
C --------------------------------------- S
protocol version

                    protocol version ok/bad    <- if bad, go to "leaving" state with reason kind "protocol version bad"

client info

                                server info    <- go to "authentication" state
```
