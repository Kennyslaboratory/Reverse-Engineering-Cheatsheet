# Linux Reverse Engineering
A full refresher for people who are stuck reversing applications off and on.  I only posted the most popular tips and tricks, so that you can quickly look at what's here and continue working.

## Disabling Linux Protections
| Protection | Command | Description |
| --- | --- | --- |
| Disable Canaries | `gcc -g overflow.c -o overflow -fno-stack-protector` | Disable stack canaries when compiling. |
| Disable ASLR | `sudo bash -c 'echo 0 > /proc/sys/kernel/randomize_va_space'` | Disables the system's ASLR protections. |

----------------------------

## Linux Debuggers
| Name | Description |
| --- | --- |
| [gdb](https://www.tutorialspoint.com/gnu_debugger/installing_gdb.htm) | GNU Debugger.  Linux's default binary debugger. |
| [gdb-peda](https://github.com/longld/peda) | A must-have extension to GDB |
| [Radare2](https://rada.re/n/radare2.html) | Reverse Engineering Framework.  One of my personal favorites.|
| [Radare2 Cutter](https://rada.re/n/cutter.html) | Radare2 GUI interface. |
| [Hopper Disassembler](https://www.hopperapp.com/) | Great GUI. Works with MacOS and Linux. |

----------------------------

## Linux Reversing Checklist
| # | Command | Description |
| --- | --- | --- |
| 1 | `file ./[file]` | Determine file type. |
| 2 | `strings ./[file]` | Print the sequences of printable characters in file. |
| 3 |  `objdump -M intel intel-mnemonic -D ./[file]   ` | Disassemble and copy entire ELF binary into a file. |
| 4 | `strace ./[file]` | Trace system calls and signals |
