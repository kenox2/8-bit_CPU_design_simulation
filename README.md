# 🧠 8-Bit CPU Design in Logisim

This project is a **custom 8-bit CPU**, designed and simulated in **Logisim**, capable of executing basic assembly-like instructions with a simple **state machine** architecture.

---

## ⚙️ Architecture Overview

- **Bus Width**: 8-bit data bus  
- **Registers**:
  - General-purpose: 5 x 8-bit registers
  - ALU-specific: `A`, `B`, and `ACC` (accumulator)
- **ALU Design**:
  - Operates on values from only **two dedicated registers**: `A` and `B`
  - Results stored in the `ACC` register
- **Instruction Format**:
  - **16-bit instructions**: Two-byte instructions with two operands
    - First 4 bits: Opcode
    - Remaining bits: Source and destination operands
  - **8-bit instructions**: Single-byte instructions with implicit operands (e.g., ALU ops)

---

## ⏱ State Machine: 3-Stage Cycle

1. **Fetch** – Instruction fetched from memory
2. **Decode** – Instruction type and operands are identified
3. **Execute** – ALU or memory/register operations are performed

---

## 🧾 Instruction Set

### 🧩 16-bit Instructions (Fetched in 2 Clock Cycles)

| Mnemonic | Opcode (4-bit) | Description                        |
|----------|----------------|------------------------------------|
| `LOAD`   | `1001`         | Load value from memory to register |
| `MOV`    | `1010`         | Move data from reg to reg/memory   |
| `STORE`  | `1011`         | Store register value to memory     |
| `JMP`    | `1100`          | Unconditional jump                 |
| `JZ`     | `1101`          | Jump if zero flag is set           |
| `JC`     | `1110`          | Jump if carry flag is set          |

> Format: `INSTR SRC, DEST`

---

### 🔧 8-bit Instructions (Fetched in 1 Clock Cycle)

| Mnemonic | Opcode (4-bit) | Description           |
|----------|----------------|-----------------------|
| `ADD`    | `0000`         | `ACC = A + B`         |
| `SUB`    | `0001`         | `ACC = A - B`         |
| `INC`    | `0010`         | `ACC = A + 1`         |
| `DEC`    | `0011`         | `ACC = A - 1`         |
| `MUL`    | `0100`         | `ACC = A * B`         |
| `AND`    | `0101`         | `ACC = A & B`         |
| `OR`     | `0110`         | `ACC = A | B`         |
| `XOR`    | `0111`         | `ACC = A ^ B`         |
| `NOT`    | `1000`         | `ACC = ~A`            |
---

## 🧪 Demo Program: Fibonacci Sequence

A demo program that calculates the **n-th Fibonacci number** has been successfully tested and run on this CPU using:

- Memory-mapped instruction storage
- Iterative loop with conditional jumps
- Register swapping and ALU operations

---

## 🚀 Getting Started
