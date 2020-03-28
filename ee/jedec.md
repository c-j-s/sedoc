JEDEC RAM/ROM/etc. pinouts
==========================

From Ciarcia, "Build an Intelligent Serial EPROM Programmer," _BYTE_
Oct. 1986, [p.106][byte-8610-106]. `O̅E̅+` is `O̅E̅/Vpp`.

    '512 '256 '128  '64 '32A  '16         '16 '32A  '64 '128 '256 '512
                                  +--∨--+
     A15  Vpp  Vpp  Vpp           | 1 28|           Vcc  Vcc  Vcc  Vcc
     A12  A12  A12  A12           | 2 27|           P̅G̅M̅  P̅G̅M̅  A14  A14
     A7   A7   A7   A7   A7   A7  | 3 26| Vcc  Vcc  N/C  A13  A13  A13
     A6   A6   A6   A6   A6   A6  | 4 25|  A8   A8   A8   A8   A8   A8
     A5   A5   A5   A5   A5   A5  | 5 24|  A9   A9   A9   A9   A9   A9
     A4   A4   A4   A4   A4   A4  | 6 23| Vpp  A11  A11  A11  A11  A11
     A3   A3   A3   A3   A3   A3  | 7 22|  O̅E̅  O̅E̅+   O̅E̅   O̅E̅   O̅E̅  O̅E̅+
     A2   A2   A2   A2   A2   A2  | 8 21| A10  A10  A10  A10  A10  A10
     A1   A1   A1   A1   A1   A1  | 9 20|  C̅E̅   C̅E̅   C̅E̅   C̅E̅   C̅E̅   C̅E̅
     A0   A0   A0   A0   A0   A0  |10 19|  D7   D7   D7   D7   D7   D7
     D0   D0   D0   D0   D0   D0  |11 18|  D6   D6   D6   D6   D6   D6
     D1   D1   D1   D1   D1   D1  |12 17|  D5   D5   D5   D5   D5   D5
     D2   D2   D2   D2   D2   D2  |13 16|  D4   D4   D4   D4   D4   D4
     GND  GND  GND  GND  GND  GND |14 15|  O3   O3   O3   O3   O3   O3
                                  +-----+
    '512 '256 '128  '64 '32A  '16         '16 '32A  '64 '128 '256 '512



<!-------------------------------------------------------------------->
[byte-8610-106]: https://archive.org/details/byte-magazine-1986-10/page/n117/mode/1up