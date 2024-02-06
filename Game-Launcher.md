1. Identification: Game connects to the launcher, sends mod version, game version. Launcher responds with implementation info.
2. Login: Launcher tells game if already logged in, if not, game sends back login details. Repeat until logged in. Launcher sends successful login response back to the game.
3. QuickJoin: Launcher tells the game whether there's already a server to connect to. If not, waits for the game to ask for something.
4. Browsing: Game can request the serverlist, or tell the launcher to connect. If so, jump to ServerIdentification.
5. ServerIdentification: Launcher sends game the server version, implementation, etc. There are several failure modes here: Failed to connect, failed to resolve, protocol version rejected, .. The launcher updates the game on changes and errors.
6. ServerAuthentication: Launcher relays the message (ok, failed, rejected) of the authentication.
7. ServerModDownload: Launcher sends status of each mod download, by sending a list of all mods and their download statuses, size, progress, speed, etc. Then sends the map to the game, and the game starts loading the map. At any time, the game can tell the launcher to go back to Browsing for any reason (this closes the connection to the server cleanly).
8. ServerSessionSetup: Get and parse players and vehicles from launcher, and send the ready packet ASAP - before spawning anything - to ensure packets are also sent asap. This may need work.
9. ServerPlaying: ... todo
10. ServerLeaving: ... todo
