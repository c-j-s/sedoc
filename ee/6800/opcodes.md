6800 Opcode Quickref
====================

This is a quick reference for hand-assembly.

    JMPᵢ  JMPₓ  BRA      JSRᵢ  JSRₓ  BSR   RTS      SWI   RTI      NOP
     BD₉   AD₈   20₄      BD₉   AD₈   8D₈   39₅      3F₁₂  3B₁₀     01₂

      Zero         Negative        Carry       oVerflow
    BEQ   BNE      BMI   BPL     BCS   BCC     BVS   BVC
     27₄   26₄      2B₄   2A₄     25₄   24₄     29₄   28₄

    unsigned         two's complement
    BLS   BHI      BLT   BLE   BGE   BGT
     23₄   22₄      2D₄   2F₄   2C₄   2E₄

    CLC   SEC   CLV   SEV   CLI   SEI
     0C₂   0D₂   0A₂   0B₂   0E₂   0F₂

    TAB   TBA   TAP   TPA   TXS   TSX      PSH A  PSH B  PUL A  PUL B
     16₂   17₂   06₂   07₂   35₄   30₄       36₄    37₄    32₄    33₄

         INC A  INC B   INX   INS   INCᵢ  INCₓ
    INC    4C₂    5C₂    08₄   31₄   7C₆   6C₇
    DEC    4A₂    5A₂    09₄   34₄   7A₆   6A₇

            #nn     zp     addr     n,X
    LDA A   86₂     96₂     B6₄     A6₅
    STA A           97₄     B7₅     A7₆
    LDA B   C6₂     D6₂     F6₄     E6₅
    STA B           D7₄     F7₅     E7₆
    LDX     CE₃     DE₄     FE₅     EE₆
    STX             DF₅     FF₆     EF₇
    LDS     8E₃     9E₄     BE₅     AE₆
    STS             9F₅     BF₆     AF₇

### Notes

- Instruction subscripts:
  - `i`: Immediate argument
  - `x`: [X] plus one-byte offset
- Opcode subscripts are cycle counts.