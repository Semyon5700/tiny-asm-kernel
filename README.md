# tiny-asm-Kernel

A minimal x86 assembly-based kernel demonstrating basic operating system concepts and interactive functionality.

## Overview

Tiny ASM Kernel is a small educational kernel written entirely in x86 assembly language. It provides a simple interactive shell with basic commands and the ability to execute raw machine code bytes.

## Features

- **Interactive Shell**: Basic command-line interface with prompt
- **Command System**: Supports multiple commands (case-insensitive):
  - `v` or `V` - Display kernel version
  - `b` or `B` - Byte execution mode (enter and execute raw machine code)
  - `p` or `P` - Print text (followed by string to display)
- **Real-time Input**: Character-by-character input with echo
- **Byte Execution**: Direct execution of hexadecimal byte sequences
- **Bootable**: Configured as a boot sector (512 bytes with boot signature)

## Technical Details

- **Architecture**: x86 (16-bit real mode)
- **Boot Method**: BIOS boot sector (MBR-style)
- **Assembly Syntax**: NASM-style
- **Memory Usage**: 
  - Input buffer: 256 bytes
  - Byte execution buffer: 16 bytes
- **BIOS Interrupts**: Uses INT 0x10 for video output and INT 0x16 for keyboard input

## Commands

### Version Command
```
Kernel> v
Ver 1.0
```

### Print Command
```
Kernel> p Hello World
Hello World
```

### Byte Execution Command
```
Kernel> b
Enter bytes: 90 (example: NOP instruction)
```
*Note: The byte buffer automatically ends with a RET instruction (0xC3)*

## Building

Requires NASM (Netwide Assembler):

```bash
nasm -f bin kernel.asm -o kernel.bin
```

## Running

You can test the kernel using an emulator like QEMU:

```bash
qemu-system-x86_64 -drive format=raw,file=kernel.bin
```

Or write to a USB drive/floppy disk for real hardware testing.

## Safety Warning

The byte execution feature allows direct execution of machine code. Use with caution as invalid instructions may cause system instability.

## Project Structure

- `kernel.asm` - Main kernel source code
- Data section: Strings and prompts
- BSS section: Input buffers
- Text section: Core functionality and command handlers

## License

This project is licensed under the GPL 3.0 License - see the LICENSE file for details.

## Author

**Semyon5700**

## Educational Purpose

This kernel is designed for educational purposes to demonstrate:
- Boot sector programming
- Basic kernel development
- x86 assembly programming
- Real-mode operating system concepts
- Interactive system programming

Perfect for learning low-level programming and operating system fundamentals!
