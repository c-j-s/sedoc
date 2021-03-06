6800 Programming Tips and Useful Routines
=========================================

See README for references not directly linked here.

_DP_ is the direct page (page 0) and its addressing mode.
±Nb,±Mc means plus or minus _N_ bytes and _M_ cycles.


General Speed and Size
----------------------

Flag bytes:
  - Clear flag: `CLR flag` (no DP, 3b/6c extended)
  - Set flag, unknown state: `TPA`, `STA flag` (3b/6c DP, 4b/7c extended)
  - Set flag, known clear: `INC flag` (no DP, 3b/6c extended)

Word increments (`INC` has no DP mode):
- `LDX, INX, STX` (5b/13c DP,   7b/15c extended)
- `INC, BEQ, INC` (6b/18c `,X`, 8b/16c extended)

Misc::
- Displacements from X are -1b/+1c from extended, ±0b/+2c from DP.
- Loading X from DP instead of immediate is -1b,+1c.
- N flag on load good for testing string termination?
