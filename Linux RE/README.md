# Linux Reverse Engineering
A full refresher for people who are stuck reversing applications off and on.  I only posted the most popular tips and tricks, so that you can quickly look at that's here and continue working.

## Disabling Linux Protections
| Protection | Command | Description |
| --- | --- | --- |
| Disable Canaries | `gcc overflow.c -o overflow -fno-stack-protector` | Disable stack canaries when compiling. |
| Disable ASLR | `sudo bash -c 'echo 0 > /proc/sys/kernel/randomize_va_space'` | Disables the system's ASLR protections. |

----------------------------

## Linux Debuggers
| Name | Description |
| --- | --- |
| gdb | GNU Debugger.  Linux's default binary debugger. |

----------------------------

## Observing ELF Metadata
| # | Title | Command | Description |
| --- | --- | --- | --- |
| 1 | Check File Type | `file ./[file]` | Determine file type |
| 2 | Check readable strings | `strings ./[file]` | Print the sequences of printable characters in file |
