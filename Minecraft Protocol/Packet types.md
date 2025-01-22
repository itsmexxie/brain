---
tags:
  - minecraft
  - packet
---
Packets types, and therefore their packet IDs, are split into different states that the protocol, or conversation, can be in. The state can be one of the following. (All of the packet tables below are specified here without their headers, but those obviously need to be included.)
# Handshaking
## Clientbound
There are no client bound packets in the Handshaking state, as the server immediately switches to the specified state.
## Serverbound
### Handshake
This packet causes the server to switch into the target state.

| **Packet ID** | **Field Name**   | **Field Type**                             | **Notes**                                                                                                                 |
| ------------- | ---------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| 0x0           | Protocol Version | [[Definitions#VarInt and VarLong\|VarInt]] | Currently 765 for version 1.20.4.                                                                                         |
| 0x0           | Server Address   | String (255)                               | Hostname or IP address that was used to connect. The Notchian server does not use this information (but must be present). |
| 0x0           | Server Port      | Unsigned Short                             | Default is 25565. The Notchian server does not use this information (but must be present).                                |
| 0x0           | Next State       | VarInt Enum                                | 1 for [[#Status]], 2 for [[#Login]]                                                                                       |
# Status
## Clientbound
## Serverbound
# Login
## Clientbound
## Serverbound
# Configuration
## Clientbound
## Serverbound
# Play
## Clientbound
## Serverbound