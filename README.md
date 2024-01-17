# Future-Spec

This repo contains the standard for BeamMP networking. The current version is in development, but is considered 1.0.0 once done. All implementations must assume 1.x.x to comply with this, at this moment.

Anyone may implement this specification in order to "speak" to either BeamMP Servers or BeamMP Launchers, or any other implementation of the spec. We, BeamMP, as authors, simply require any implementation to adhere **exactly** to the specification, and identify itself in the `ServerInfo` and `ClientInfo` packets in the `Identification` state.
