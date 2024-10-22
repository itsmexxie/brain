---
tags:
  - minecraft
---
# Data Types
# VarInt and VarLong
These types are used for encoding variable length numbers, so that we don't have to choose a high bit number format to allow for large numbers, such as u64, but at the same time smaller numbers don't take up more bytes than needed.

The least 7 significant bits are used to encode the value and the most significant bit indicates whether there's another byte that was used to encode the number. The least significant group is written first, which means that VarInts are effectively little endian.

VarInts are never longer than 5 bytes ($2^{35} - 1$), and VarLongs are never longer than 10 bytes ($2^{70} - 1$).

Here's a pseudocode snippet for reading and writing VarInts & VarLongs.

```c
static final int SEGMENT_BITS = 0b01111111; // 0x7F
static final int CONTINUE_BIT = 0b10000000; // 0x80
```

```c
public int readVarInt() {
    int value = 0;
    int position = 0;
    byte currentByte;

    while (true) {
        currentByte = readByte();
        value |= (currentByte & SEGMENT_BITS) << position;

        if ((currentByte & CONTINUE_BIT) == 0) break;

        position += 7;

		if (position >= 32) {
			throw new RuntimeException("VarInt is too big");
		}
    }

    return value;
}
```