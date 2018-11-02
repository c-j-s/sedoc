Logic Gates
-----------

    0 1 0 1      A
    0 0 1 1  in  B
    -----------------------------------
    0 0 0 0   ₀  FALSE    A•¬A
    1 1 1 1   ₀  TRUE     A+¬A
    0 1 0 1   ₁  A        A
    1 0 1 0   ₁  NOTA     ¬A
    0 0 1 1   ₁  B        B
    1 1 0 0   ₁  NOTB     ¬B
    0 0 0 1      AND      A•B
    1 1 1 0      NAND     ¬(A•B)
    0 1 1 1      OR       A+B
    1 0 0 0      NOR      ¬(A+B), ¬A•¬B
    0 1 1 0      XOR      A⊕B, A≠B
    1 0 0 1      XNOR     A=B               IFF, biconditional
    0 1 0 0               A•¬B
    0 0 1 0               ¬A•B
    1 1 0 1               A+¬B
    1 0 1 1               ¬A+B

Adders
------

### Half Adder

    0 1 0 1     A
    0 0 1 1     B
    ----------------------------   
    0 0 0 1     C  carry    A•B
    0 1 1 0     S  sum      A⊕B

#### Full Adder

    0 1 0 1  0 1 0 1  A
    0 0 1 1  0 0 1 1  B
    0 0 0 0  1 1 1 1  Carry
    --------------------------------------------------------
    0 0 0 1  0 1 1 1  C     A•B⊕C       A•B + C•(A⊕B)
    0 1 1 0  1 0 0 1  S     A⊕B⊕C       C•¬(A⊕B) + ¬C•(A⊕B)

* Make from two half adders:
  - A1•B1 = S1 → A2
  - A2⊕B2 → Sum
  - Carry input → B2
  - A2•B2 → C2
  - C1+C2 → Carry Output (short for wired-OR, assuming no backfeed)