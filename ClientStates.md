## ClientStates

A ClientState represents the state in which both the launcher and game are, in relation to each other.

1. `ClientIdentification = 0xC0`: Game connects to the launcher, sends mod version, game version. Launcher responds with implementation info.
2. `Login = 0xC1`: Launcher tells game if already logged in, if not, game sends back login details. Repeat until logged in. Launcher sends successful login response back to the game.
3. `QuickJoin = 0xC2`: Launcher tells the game whether there's already a server to connect to. If not, waits for the game to ask for something.
4. `Browsing = 0xC3`: Game can request the serverlist, or tell the launcher to connect. If so, jump to ServerIdentification.
5. `ServerIdentification = 0xC4`: Launcher sends game the server version, implementation, etc. There are several failure modes here: Failed to connect, failed to resolve, protocol version rejected, .. The launcher updates the game on changes and errors.
6. `ServerAuthentication = 0xC5`: Launcher relays the message (ok, failed, rejected) of the authentication.
7. `ServerModDownload = 0xC6`: Launcher sends status of each mod download, by sending a list of all mods and their download statuses, size, progress, speed, etc. Then sends the map to the game, and the game starts loading the map. At any time, the game can tell the launcher to go back to Browsing for any reason (this closes the connection to the server cleanly).
8. `ServerSessionSetup = 0xC7`: Get and parse players and vehicles from launcher, and send the ready packet ASAP - before spawning anything - to ensure packets are also sent asap. This may need work.
9. `ServerPlaying = 0xC8`: ... todo
10. `ServerLeaving = 0xC9`: ... todo
