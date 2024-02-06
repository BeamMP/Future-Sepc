## 1. Identification

The identification state's purpose is:

- The client informing the server of program version, protocol version, game version, mod version and implementation (more info on this further down)
- The server informing the client of program version, confirming/denying support for the protocol version, and informing of implementation

### Purposes

```
 1          Protocol version
 2          Protocol version ok
 3          Protocol version bad
 4          Client info
 5          Server info
???         Request Server details
???         Server details
```

### Formats

#### Protocol version

```
|       6       |
+---------------+
|    version    |
+---------------+
```

#### Client/Server info format

##### Client info

```
|       6       |       6       |       6       |      ...       |
+---------------+---------------+---------------+----------------+
|  prog version |  game version |  mod version  | implementation |
+---------------+---------------+---------------+----------------+
```

##### Server info

```
|       6       |      ...       |
+---------------+----------------+
|  prog version | implementation |
+---------------+----------------+
```

#### Versions format

Each version is represented by 6 bytes, binary, unsigned, little endian, as follows:

```
|    1    |    2    |    3    |    4    |    5    |    6    |
+---------+---------+---------+---------+---------+---------+
|      major        |       minor       |       patch       |
+-------------------+-------------------+-------------------+
```

#### Implementation format

An ASCII string of at most 254 characters, prefixed by the length in one byte, **not** null-terminated.

```
|    1    |  2...   |
+---------+---------+
|   size  |   ...   |
+---------+---------+
```

### Protocol

```
C --------------------------------------- S
protocol version

                    protocol version ok/bad    <- if bad, connection close

client info

                                server info    <- go to "authentication" state
```
