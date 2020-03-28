Apple II Monitor
================

Monitor Commands
----------------

`CALL -151` (65385, $FF69) enters monitor, giving a `*` prompt. Exit
with Ctrl-Reset (uses vector at $3F2), Ctrl-C + Enter or `3D0G` (runs
the resident program, usually Applesoft, which has set up a `JMP`
instruction at $3D0). Loading `69 FF 5A` at $3F2 will make Ctrl-Reset
bring up the monitor.

If the monitor was entered via a `BRK` ($00) instruction and `FF 69`
at the break vector $3F0‥$3F1, the registers registers A, X, Y, P
(status), S (stack) at entry are stored at location $45‥$49.

Multiple commands may be entered on a single line, separated by
spaces. `:` must end with a commant >`F`; `N` is good for this.

"_+:_" indicates a feature available only in version 00 or higher of
the Apple IIc ROM.

Misc. commands:
- `n+m` and `n-m` do 8-bit two's-complement arithmetic.
- `N`, `I`: Normal and inverse display mode.
- `port^P` and `port^K` set output and input to _port_.

Memory commands:
- All commands may preceeded by a hex value, e.g., `E000` to set the
  "last opened location" (_last_) and the "next changable location"
  (_next_), which is the addresss used for any subsequent command.
  Otherwise the previously set _last_ is used.
- A CR displays the byte at _last_ and increments _last_.
- Enter or a single hex value displays the byte at that address and
  sets _last_ and _next_ to the following address.
- `.` followed by an address displays memory from _last_ to that
  address. _last_ and _next_ are both the last location displayed.
- `L` disassembles ("lists") 20 instructions starting at the address
  given or the current program counter (stored at $3A).
- `:` followed by space-separated hex numbers (`3e 3f`) (_+:_ or
  single-quote followed by a character: `'A 'B`) deposits that byte at
  _next_.
- _+:_ `!` starts the mini-assembler (prompt `!`). Enter `addr:inst
  args` to assemble an instruction; space for _addr_ uses the next
  location. All numbers are in hex; `$` prefixes are optional.
- `dest<start.endM` moves memory from _start_ to _end_ to locations
  starting at _dest_ (the _dest_ range may overlap the source range)
  and sets _last_ to the last location read and _next_ to the last
  location written.
- `dest<start.endV` compares ("verifies") memory. Non-matching
  source/dest bytes will be displayed like `02FB-0B (0A)`.
- `^E` displays the register values A,X,Y,P,S from locations $45‥49
  and sets _next_ to $45. (_+:_ This includes the IIe/IIc `M` memory
  state from $44; see [a2cref-355].)

Execution and exit commands:
- `G` starts executing at _next_. `RTS` or `BRK` will return to the
  monitor; the latter displays the PC and registers.
- _+:_ `S` steps one instruction; `T` traces execution until
  solid-apple is pressed or `BRK` is executed (`RTS` will not return
  to the monitor). Holding open-apple will slow the trace to one step
  per second.
- `^Y` jumps to $3F8.
- Ctrl-B: Cold start current interpreter (usually BASIC, w/DOS if
  loaded; default $E000).
- Ctrl-C: Warm start current interpreter (default $E003).
- `3D0G`: Re-enter DOS interpreter.

Tricks:
- Setting location $34 (`34:n`) sets the current read position in the
  input buffer; this can be used to repeat commands by following it
  with a space, e.g., `L 34:0 `. Ctrl-Reset stops the loop.

Detailed documentation is in [Chapter 10][a2cref-c10] of the _Apple
IIc Technical Reference Manual_. Also see [Apple-II
Mini-Assembler][a2mini-asm] instructions and listing.



<!-------------------------------------------------------------------->
[a2cref-355]: https://archive.org/details/Apple_IIc_Technical_Reference_Manual/page/n362
[a2cref-c10]: https://archive.org/details/Apple_IIc_Technical_Reference_Manual/page/n230
[a2mini-asm]: https://archive.org/details/Apple2_Woz_MiniAssembler/page/n1/mode/1up