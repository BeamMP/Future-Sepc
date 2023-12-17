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

