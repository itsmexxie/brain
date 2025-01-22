---
tags:
  - minecraft
  - packet
---
# Basic format
The length of the packet is limited by the maximum that a 3-byte *[[Definitions#VarInt and VarLong|VarInt]]* can represent, which means it cannot exceed $2^{21} - 1$ or 2097151 bytes. This applies to **both** compressed and uncompressed lengths.

Once a *Set Compression* packet has been sent, all following packets will be compressed by **zlib**. The format of the packet changes slightly. If the data length of the packet is smaller than the threshold specified in the compression packet, then it will be sent uncompressed.

Compression can be turned off by sending a *Set Compression* packet with a negative threshold.

Packets are split into different states of the conversion. Packet IDs differ between these states, and so it is important to pay close attention to which state the conversion is currently in.
## Without compression 
| **Field Name** | **Field Type** | **Notes** |
| ---- | ---- | ---- |
| Packet Length | VarInt | Length of Packet ID + Data |
| Packet ID | VarInt | ID of packet |
| Data | Byte Array | Depends on the connection state and packet ID |
## With compression
| **Field Name** | **Field Type** | **Compressed** | **Notes** |
| ---- | ---- | ---- | ---- |
| Packet Length | VarInt | No | Length of (Data Length)  + compressed length of (Packet ID + Data) |
| Data Length | VarInt | No | Length of uncompressed Packet or 0 |
| Packet ID | VarInt | Yes | Compressed Packet ID (zlib) |
| Data | Byte Array | Yes | Compressed Data (zlib) |