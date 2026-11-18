# TP VHDL & PROGRAMMABLE DIGITAL CIRCUITS
#### Authors <br>
Jesper **Nytun** <br>
Peder **Trones** <br>

#### Background

RISC Microprocessor with five pipeline stages made with VHDL. Consisting of a ALU, a register bank, and seperate data and instruction memory. Done as coursework as part of our 7th semester at INSA Toulouse. <br>
****

## Instructions
List of accessible operations in our Microprocessor
| Operation | Code | Instruction format | Description |
|---|---|---|---|
| Addition | `0x01` | `ADD Ri Rj Rk` | `[Ri] ← [Rj] + [Rk]` |
| Multiplication | `0x02` | `MUL Ri Rj Rk` | `[Ri] ← [Rj] * [Rk]` |
| Subtraction | `0x03` | `SOU Ri Rj Rk` | `[Ri] ← [Rj] - [Rk]` |
| AND | `0x14` | `AND Ri Rj Rk` | `[Ri] ← [Rj] and [Rk]` |
| OR | `0x15` | `OR Ri Rj Rk` | `[Ri] ← [Rj] or [Rk]` |
| XOR | `0x16` | `XOR Ri Rj Rk` | `[Ri] ← [Rj] xor [Rk]` |
| NOT | `0x17` | `NOT Ri Rj _` | `[Ri] ← not [Rj]` |
| Copy | `0x05` | `COP Ri Rj _` | `[Ri] ← [Rj]` |
| Assign (load constant) | `0x06` | `AFC Ri j _` | `[Ri] ← j` |
| Load | `0x07` | `LOAD Ri @j _` | `[Ri] ← [@j]` |
| Store | `0x08` | `STORE @i Rj _` | `[@i] ← [Rj]` |

## Results
TBA
## Architecture

### ALU - Arithmetic Logic Unit
The ALU is designed as following
|I/O| Function|
|---|---|
| A, B | Input Register |
| Ctrl_ALU | Operator Select |
| S | Output Register |
| N, O, C | Flags: Negative, Overflow and Carry |

``` vhdl
entity ALU is
    Port ( A : in STD_LOGIC_VECTOR (7 downto 0);
           B : in STD_LOGIC_VECTOR (7 downto 0);
           Ctrl_ALU : in STD_LOGIC_VECTOR (2 downto 0);
           S : out STD_LOGIC_VECTOR (7 downto 0);
           N : out STD_LOGIC;
           O : out STD_LOGIC;
           C : out STD_LOGIC);
end ALU;

```

### Register Bank
| I/O | Function |
|---|---|
| addrA, addrB | Read Adresse |
| addrW | Write Address |
| W | Write Enable|
| DATA | Data Input |
| RST | Reset |
| CLK | Clock |
| QA, QB | Output Registers A and B |

```vhdl
entity Register_bank is
    Port ( addrA : in STD_LOGIC_VECTOR (3 downto 0);
           addrB : in STD_LOGIC_VECTOR (3 downto 0);
           addrW : in STD_LOGIC_VECTOR (3 downto 0);
           W : in STD_LOGIC;
           DATA : in STD_LOGIC_VECTOR (7 downto 0);
           RST : in STD_LOGIC;
           CLK : in STD_LOGIC;
           QA : out STD_LOGIC_VECTOR (7 downto 0);
           QB : out STD_LOGIC_VECTOR (7 downto 0));
end Register_bank;
```

### Instruction memory

| I/O | Function |
|---|---|
| ADDRESS | Instruction Address |
| CLK | Clock |
| O | Instruction Output |

```vhdl
entity Instruction_memory is
    Port ( ADDRESS : in STD_LOGIC_VECTOR (7 downto 0);
           CLK : in STD_LOGIC;
           O : out STD_LOGIC_VECTOR (31 downto 0));
end Instruction_memory;
```

### Data memory

| I/O | Function |
|---|---|
| ADDRESS | Data Address |
| I | Data Input |
| RW | Read/Write Select |
| RST | Reset |
| CLK | Clock |
| O | Data Output |

```vhdl
entity Data_memory is
    Port ( ADDRESS : in STD_LOGIC_VECTOR (7 downto 0);
           I : in STD_LOGIC_VECTOR (7 downto 0);
           RW : in STD_LOGIC;
           RST : in STD_LOGIC;
           CLK : in STD_LOGIC;
           O : out STD_LOGIC_VECTOR (7 downto 0));
end Data_memory;
```

## Lessons
TBA
