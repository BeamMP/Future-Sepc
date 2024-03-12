# Endpoints

There are several endpoints the Launcher and Server have to talk to. These must be used in the ways specified here. Abusing the endpoints (for example by not honoring the here imposed rates / rate limits, etc.) can lead to your server or your account to be blacklisted or or removed from our systems. Adherance to the protocol is strictly required, and the use of these endpoints is, too.

## Login

Only used by the Launcher/client.

The `auth.beammp.com/userlogin` endpoint takes either 1) a username and password `{ "username": ..., "password": ... }` or 2) a private key `{ "pk": ... }`. Option 1) must only be used if option 2) fails due to an expired private key. Both return both the public and private key, as well as general login information. The guest login endpoint is not specified here yet // TODO.

Logins must be kept within a limit of at most X requests per minute. All login attemps must be well-intentioned and only to accounts owned by the user. Only real human users are allowed to use these endpoints (// TODO).

## Authentication

Only used by the Server.

The `auth.beammp.com/pkToUser` endpoint is used to verify a public key corresponds to a single user. These public keys are assumed to be single use. The same rules for use of this apply as for login. Although we do not impose a rate limit, we require that all requests fall under fair use of the endpoint - if an unreasonable number of requests is made, we still consider it abuse. A server should talk to this endpoint as part of the Authentication state, and no other situation.

## Heartbeat

Only used by the Server.

The heartbeat `backend.beammp.com/heartbeat` endpoint takes www-urlencoded parameters:

- uuid= The AuthKey of the server, obtained at `keymaster.beammp.com`
- players= How many players are on this server
- maxplayers= How many players are allowed in the server at one time
- port= TCP and UDP listen port
- map= Map string
- private= Whether the server should appear on the list (false = appear on the list)
- version= MAJOR.MINOR.PATCH version of the server
- clientversion= MAJOR.MINOR version of the launcher required to access the server
- name= Name of the server
- tags= Comma-separated list of tags
- modlist= Comma-separated list of mod file names
- modstotalsize= Total size in bytes of all mods
- modstotal= How many mods
- playerslist= A comma-separated list of names of players on the server
- desc= Description of the server

It takes a HTTP header with key `api-v`, the value of which is `2`.

A server must adhere to these strict limits:
- One request every 1 minute by default
- If `players`, `playerslist`, `private` or `port` changed, the server may heartbeat more than once in a minute, *but* every heartbeat **must** be spaced out at least 5 seconds from the last heartbeat. If multiple heartbeats are sent within a minute without the data changing significantly, the beammp backend will  consider the behavior abusive.
- If a heartbeat fails, the server may only retry at most once every 5 seconds. If the outage continues more than a few heartbeats, the server must exponentially increase the time between heartbeats back up to once per minute.
