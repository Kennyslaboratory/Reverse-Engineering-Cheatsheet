# Windows Reverse Engineering
Windows applications make calls to the Windows API in order function.  To my knowledge, all Windows APIs are called and processed internally, even if the application is using .NET or the C++ library, Microsoft Foundation Class Library (MFC).  The API is being used in some way, therefore, it is in out best interest to do `API Hooking`.  These days, Microsoft is promoting the use of the .NET Framework for developing Windows applications. The .NET Framework uses the `System` class for accessing the Win32 API.

If you’re going to be doing serious reversing of Windows applications, it is going to be important for you to understand the Win32 API because no matter which high-level interface an application employs (if any), it is eventually going to use the Win32 API for communicating with the OS

## Windows API Main Components
| Component | Description | Mode |
| --- | --- | --- |
| Kernel32.dll | Base API Client Component. Non-GUI-related services, such as file I/O, memory management, object management, process and
thread management. | User-Mode |
| Ntdll.dll | Native API Interface. Supports any number of application-level subsystems. | User-Mode |
| User32.dll | The User API Client Component. Includes functionality for window management, message passing, input processing and standard controls. | User-Mode |
| GDI32.dll | Graphics Device Interface (GDI) API Client Component. Exports functions that perform primitive drawing functions. | User-Mode |
| WIN32K.sys | The Win32 Kernel Implementation.  Informally WinAPI, is Microsoft's core set of application programming interfaces (APIs) | Kernel-Mode |
| NTOSKRNL.exe | The Windows Kernel. Responsible for various system services such as hardware abstraction, process and memory management, thus making it a fundamental part of the system. | Kernel-Mode |


## API Hooking
API hooking is a technique by which we can instrument and modify the behavior and flow of API calls. Hooking can be used to introspect calls in a Windows application or can be used to capture some information related to the API Calls.  It will help that you understand DLL Logic and System Calls beforehand.

### Creating a Fake DLL
The method of hooking the API through the DLL.  For example, create a fake DLL that has exactly the same export function as `kernel32.dll` and has exactly the same behavior, and make the exe file recognize the DLL as if it were a real kernel32.dll. So I was hooking the API call. In other words, the API hook was realized by mediating the DLL we prepared. This method is Mendokusai, but it is simple, easy to understand, and can be used as an easy way to hook the API.However, when hooking a function in a DLL that controls the core of Windows, such as kernel32.dll or user32.dll, it is a surprisingly time-consuming technique, such as having to change the contents of the exe file itself by only one byte ...

By the way, it seems that this technique is sometimes called "DLL Injection", but in my sense, " DLL in the running process" that was dealt with in "Resident Program Concealment Technique" of "Wizard Bible vol.10" "Injecting" "was called" DLL Injection ", so for convenience, this technique will be called" DLL-mediated API hook ". Well, it doesn't matter what you call it, but it would be inconvenient if both were called the same (^) ^;
