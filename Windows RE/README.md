# Windows Reversing Tools
| # | Toolkit | Description |
| --- | --- | --- |
| 1 | [FlareVM](https://github.com/fireeye/flare-vm) | Windows Reverse Engineering Suite. |
| 2 | [Windows Sysinternals](https://docs.microsoft.com/en-us/sysinternals/) | Tools created by Microsoft for Debugging and Binary Analysis. |
| 3 | [Immunity Debugger](https://www.immunityinc.com/products/debugger/) | Free and power debugger.  Used by the [Corelan Team](https://www.corelan.be/index.php/about-us/about-corelan-team/). |

# Hex Translations Tools
| Tool | Description |
| --- | --- |
| [Online Hex Tools](https://onlinehextools.com/) | Useful online tools for translating memory, etc. |
| [Unitconverters](https://www.unitconverters.net/numbers/base-10-to-base-8.htm) | Quick and Simple translations |

# Windows Reverse Engineering
Windows applications make calls to the Windows API in order function.  To my knowledge, all Windows APIs are called and processed internally, even if the application is using .NET or the C++ library, Microsoft Foundation Class Library (MFC).  The API is being used in some way, therefore, it is in our best interest to do `API Hooking` in some cases. 

By the way, these days Microsoft is promoting the use of the .NET Framework for developing Windows applications. The .NET Framework uses the `System` class for accessing the Win32 API and is higher-level than MFC / C++.

If you’re going to be doing serious reversing of Windows applications, it is going to be important for you to understand the [Win32 API](https://docs.microsoft.com/en-us/windows/win32/apiindex/windows-api-list) because no matter which high-level interface an application employs (if any), it is eventually going to use the Win32 API for communicating with the OS

## Windows API Main Components
| Component | Description | Mode |
| --- | --- | --- |
| [Kernel32.dll](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files#KERNEL32.DLL) | Base API Client Component. Non-GUI-related services, such as file I/O, memory management, object management, process and thread management. | User-Mode |
| [Ntdll.dll](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files#NTDLL.DLL) | Native API Interface. Supports any number of application-level subsystems. | User-Mode |
| [User32.dll](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files#USER32.DLL) | The User API Client Component. Includes functionality for window management, message passing, input processing and standard controls. | User-Mode |
| [GDI32.dll](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files#GDI32.DLL) | Graphics Device Interface (GDI) API Client Component. Exports functions that perform primitive drawing functions. | User-Mode |
| [WIN32K.sys](https://en.wikipedia.org/wiki/Windows_API) | The Win32 Kernel Implementation.  Informally WinAPI, is Microsoft's core set of application programming interfaces (APIs) | Kernel-Mode |
| [NTOSKRNL.exe](https://en.wikipedia.org/wiki/Ntoskrnl.exe) | The Windows Kernel. Responsible for various system services such as hardware abstraction, process and memory management, thus making it a fundamental part of the system. | Kernel-Mode |


## API Hooking
API hooking is a technique by which we can instrument and modify the behavior and flow of API calls. API Hooking can be used to intercept calls in a Windows application or can be used to capture some information related to the API Calls.  It will help that you understand DLL Logic and System Calls beforehand.

### Hook Types
| Type | Description |
| --- | --- |
| Local Hooks | These influence only specific applications. |
| Global hooks | These affect all system processes. |

### DLL Injection - (Creating a Fake DLL)
The method of hooking the API through a DLL, also called, "DLL Injection".  For example, we can create a fake DLL that has exactly the same export function as `kernel32.dll` and has exactly the same behavior, and make the .exe file recognize the DLL as if it were a real `kernel32.dll`.

**4 Steps of DLL Injection**
  - **Attach** to the process
  - **Allocate** Memory within the process
  - **Copy the DLL** or the DLL Path into the processes memory and determine appropriate memory addresses
  - **Instruct the process** to Execute your DLL

## Useful Windows API Functions - (DLL Injection)
| Function | Description |
| --- | --- |
| LoadLibraryA() | Automatically load a library.  Easy to use but very easy to block and detect. |
| GetProcAddress() | Retrieves the address of an exported function or variable from the specified dynamic-link library (DLL). |
| CreateToolhelp32Snapshot() | Takes a snapshot of the specified processes, as well as the heaps, modules, and threads used by these processes. |
| OpenProcess() | Opens an existing local process object. |

## LoadLibraryA()
`LoadLibraryA()` is a `kernel32.dll` function used to load DLLs, executables, and other supporting libraries at run time.  It's super easy and allows you to get your DLL injected without manual mapping.  The down side is that using this function is really easy to detect and stop because it registers the loaded DLL with the program.

Programmers can detect a `LoadLibraryA()` by using the [CreateToolhelp32Snapshot()](https://docs.microsoft.com/en-us/windows/win32/api/tlhelp32/nf-tlhelp32-createtoolhelp32snapshot), [EnumProcessModules()](https://docs.microsoft.com/en-us/windows/win32/api/psapi/nf-psapi-enumprocessmodules), and [NtQueryVirtualMemory()](https://docs.microsoft.com/en-us/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntqueryvirtualmemory) functions.

The only parameter `LoadLibraryA()` needs however is the filename.  This means that we just need to allocate some memory for the path to our DLL and set our execution starting point to the address of LoadLibraryA(), providing the memory address where the path lies as a parameter. However, a slightly annoying caveat with `LoadLivraryA()` is that if a DLL has already been loaded once with it, it will not execute it. You can work around this issue but it will require more code.

## Jumping to DllMain - (Manual Mapping)
An alternative method to `LoadLibraryA()` is load the entire DLL into memory, then determine the offset to the DLL's entry point. Using this method you can avoid registering the DLL with the program (stealthy) and repeatedly inject into a process.

... *[to be continued]* ...


# Resources Referenced
| # | Resource |
| --- | --- |
| 1 | [Apriorit](https://www.apriorit.com/dev-blog/160-apihooks) |
| 2 | [Secrets_of_Reverse_Engineering](https://www.foo.be/cours/dess-20122013/b/Eldad_Eilam-Reversing__Secrets_of_Reverse_Engineering-Wiley(2005).pdf) |
| 3 | [Open Security Blog](http://blog.opensecurityresearch.com/2013/01/windows-dll-injection-basics.html) |
