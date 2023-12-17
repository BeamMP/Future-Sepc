## 3. Mod Download

The mod download state handles syncing of mods needed to join the server (e.g. maps).

The server can specify how the client must download the mods present.

### Server mods info format

The server mods info packet specifies:

- The maximum ($max$) amount of parallel connections ($n$) the client is allowed to open (so the client must open $1 \le n \le max$ connections)
- 
