# States

Each client form the server-side view is considered to be in exactly one state at any time.
The state dictates which packets are handled and how they are handled - for example, a packet with purpose 1234 might mean something in mod download, but also in gameplay, and that's fine because they exist in entirely different states.

State changes needs to happen atomically, the server is the authority on this.
Specific packets in each state trigger a state change, and the clients must never send any packets for a previous state while knowingly being in a new state.

The usual BeamMP join/play/leave loop has the following states:

1. Identification
2. Authentication
3. Mod download
4. Session setup
5. Playing
6. Leaving

The state change packet is sent by the server to indicate that the state has been changed:

Purpose:

```
0xaa02   State change to Authentication
0xaa03   State change to ModDownload
0xaa04   State change to SessionSetup
0xaa05   State change to Playing
0xaa06   State change to Leaving
```
