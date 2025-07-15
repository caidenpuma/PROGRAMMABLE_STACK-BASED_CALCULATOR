# Stack-Based Calculator (Postfix Calculator)

## Overview

This project implements a programmable stack-based calculator that performs 8-bit integer arithmetic using postfix notation. The calculator was designed for the EN1640 Computer System Design course at Brown University and executes programs stored in ROM memory.

## Features

- **Stack-based architecture** with 10 8-bit entries
- **Postfix notation** for arithmetic expressions
- **Real-time display** of stack top on 7-segment display
- **Overflow detection** for addition and subtraction operations
- **FPGA implementation** with optimized resource usage (83 ALMs)
- **ROM-based program storage** with .mif file initialization

## Supported Instructions

| Instruction | Opcode | Description |
|-------------|---------|-------------|
| `push value` | Custom | Push immediate 8-bit value onto stack |
| `add` | Custom | Pop two values, push sum |
| `sub` | Custom | Pop two values, push difference |
| `mult` | Custom | Pop two values, push product |
| `halt` | Custom | Stop execution, display result |

## Architecture Components

### Core Modules
1. **Main Module** - Top-level integration of all components
2. **ALU Module** - Performs arithmetic operations and stack management
3. **Display Module** - Converts binary to BCD and drives 7-segment display
4. **Double Dabble Module** - Binary to BCD conversion algorithm
5. **ROM Interface** - Program memory storage and instruction fetching

### Key Design Features
- **10-entry stack** - Sufficient for complex arithmetic expressions
- **Overflow detection** - LED indicator for arithmetic overflow
- **Decimal display** - Shows results in human-readable format
- **Program counter** - Tracks instruction execution sequence
- **Memory-mapped instructions** - ROM-based program storage

## Example Programs

### Example A: 8 - 5 * 3 = -7
```assembly
push 8
push 5
push 3
mult      # Stack: [8, 15]
sub       # Stack: [-7]
halt      # Display: -7
```

### Example B: 5 + ((1 + 2) * 4) - 3 = 14
```assembly
push 5
push 1
push 2
add       # Stack: [5, 3]
push 4
mult      # Stack: [5, 12]
add       # Stack: [17]
push 3
sub       # Stack: [14]
halt      # Display: 14
```

## Performance Metrics

- **Resource Utilization**: 83 ALMs (under 67 ALM optimization target)
- **Stack Depth**: 10 entries maximum
- **Data Width**: 8-bit arithmetic
- **Display**: 3-digit decimal output with sign

## Getting Started

### Prerequisites
- Intel Quartus Prime (for FPGA synthesis)
- ModelSim (for simulation)
- Compatible FPGA board with 7-segment displays

### Setup Instructions
1. Extract the `.qar` file in Quartus Prime
2. Compile the project to generate the FPGA bitstream
3. Program the FPGA board
4. Load test programs using .mif files
5. Monitor execution on 7-segment displays

### Creating Custom Programs
1. Write assembly code using supported instructions
2. Convert to machine code using your instruction format
3. Create .mif file with machine code
4. Load into ROM and execute

## Instruction Set Architecture

### Instruction Format
Custom instruction encoding designed for efficient stack operations:
- **Immediate values**: Encoded with push instruction
- **Operation codes**: Unique opcodes for each arithmetic operation
- **Stack-based**: No register addressing needed

### Stack Operations
- **Push**: Shifts existing values down, adds new value at top
- **Pop**: Removes top value, shifts remaining values up
- **Arithmetic**: Pops operands, pushes result

## Verification

The design has been verified with:
- **Testbench simulation** for both example programs
- **Waveform analysis** using Quartus waveform editor
- **FPGA testing** with actual hardware implementation
- **Result validation** against hand calculations

### Test Results
- **Example A**: Correctly outputs -7
- **Example B**: Correctly outputs 14
- **Overflow detection**: LED activates for arithmetic overflow
- **Display functionality**: Proper decimal representation

## Design Optimizations

Key optimizations implemented to achieve <67 ALM target:
- **Efficient stack management** - Minimized logic for stack operations
- **Optimized ALU design** - Reused components from Assignment 02
- **Streamlined display logic** - Efficient BCD conversion
- **ROM interface optimization** - Minimal control logic

## Hardware Implementation

### Display System
- **7-segment displays** - Three digits for decimal output
- **Sign indication** - Proper negative number display
- **Real-time update** - Continuous stack top monitoring

### Memory System
- **ROM storage** - Program instructions in .mif format
- **Stack memory** - 10 8-bit entries in registers
- **Program counter** - Instruction sequencing

## Limitations

- **8-bit arithmetic** - Limited number range (-128 to 127)
- **10-entry stack** - Maximum expression complexity
- **No floating-point** - Integer arithmetic only
- **Simple instruction set** - Basic arithmetic operations only

## Future Enhancements

Potential improvements for extended versions:
- **16-bit or 32-bit arithmetic** - Extended number range
- **Additional operations** - Division, modulo, bitwise operations
- **Larger stack** - Support for more complex expressions
- **Subroutine support** - Function calls and returns
- **Memory operations** - Load/store instructions

## Testing and Validation

### Simulation Results
- **ModelSim testing** - Comprehensive functional verification
- **Waveform analysis** - Signal timing verification
- **Edge case testing** - Overflow and underflow conditions

### Hardware Validation
- **FPGA deployment** - Real hardware testing
- **Display verification** - Correct decimal output
- **Performance analysis** - Resource utilization optimization
