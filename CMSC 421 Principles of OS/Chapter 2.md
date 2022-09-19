# Chapter 2 OS Structures

## OS Services
- Provide an environment for execution of programs and services to programs and users
- One set of OS services provies functions that are helpful to the user.
	- **User Interface** - Almost all OSs have a UI
	- **Program Execution** - The system must be able to load a program into memory and to run that program, end execution, either normally or abnormally (indicating error)
	- **IO Ops** - A running program may require IO, whcih may involve a file or an IO device
	- **FS manipulation** - The fs is of particular interest. Programs need to read and write files and directories create and delete them, search them, list file information, permission management.
	- **Communications** - Processes may exchance information, on the same computer or between computers over a network.
	- **Error Detection** - OS needs to be constantly aware of possible errors
- Another set of OS functions exists for ensuring the efficient operation of the system itself via resource sharing
	- **Resource Allocation** - When multiple users or multiple jobs running concurrently, resources must be allocated to each of them
	- **Logging** - To keep track of which users use how much and what kinds of computer resources
	- **Protection and security** - The owners of information stored in a multiuser or networked computer system may want to control use of that information, concurrent processes should not interfere with each other
	- ![[Pasted image 20220914103138.png]]
## User and OS Interface
- CLI or **Command interpreter** allows direct command entry
	- Sometimes implemented in kernel, sometimes by systems program
	- Sometimes multiple flavors implemented - **Shells**
	- Primarily fetches a command from user and executes it
	- Sometimes commands built-in, sometimes just names of programs
		- If the latter adding new features doesn't require shell modification
- User-friendly **desktop** metaphor interface
	- Usually mouse, keyboard, and monitor
	- **Icons**
	- Various mouse buttons over objects in the interface cause various actions (provide information, options, execute function, open directory)
	- Invented at Xerox PARC
- Many systems now include both CLI and GUI interfaces
	- WIndows is GUI with CLI "command" shell
	- MacOS X is "Aqua" GUI interface with UNIX kernel underneath and shells available
	- Unix and Linux have CLI with optional GUI interfaes (CDE, KDE, GNOME)ha
## System Calls
- Programming interface to the services provided by the OS
- Typically written in a high-level language (C or C++)
- Mostly accessed by programs via a high-level **Application Programming Interface (API)** rather than direct syscall use
- Three most common APIs are Win32 API for windows, POSIX API for POSIX-based systems, and Java API for the JVM
- ![[Pasted image 20220914104942.png]]
- ![[Pasted image 20220914105007.png]]
### Implementation
- Typically a number associated with each system call
	- **System-call Interface** maintains a table indexed according to these numbers
- The system call interface invokes the intended system call in OS kernel and returns status of the syscall and any return values
- The caller need know nothing about how the syscall is implemented
	- Just needs to obey API and understand what OS will do as a result call
	- Most details of OS interface hidden from programmer by API
- ![[Pasted image 20220914105439.png]]
### Parameter Passing
- Often, more information is required than simply identity of desired syscall
	- Exact type and amount of information vary according to OS and call
- Three general methods used to pass parameters to the OS
	1. Simplest: pass the parameters in registers
	2. Parameters stored in a block, or table, in memory, and address of block passed as a parameter in a register
	3. Parameters placed, or **pushed**, onto the **stack** by the program and **popped** off the stack by the OS
	- Block and stack methods do not limit the number or length of parameters being passed
### Types
- Process control
- File management
- Device management
- Information maintenance
- Communications
- Protection
## System Services
- Systems programs provide a convenient environment for program development and execution. They can be divided into:
- Most users' view of the OS is defined by system programs, not the actual syscalls
- **Background Services**
	- Launch at boot time
	- Provide facilities like disk checking, process scheduling, error logging, printing
	- Run in user context not kernel context
	- Known as services, subsystems, and daemons
## Linkers and Loaders
- Source code compiled into object files designed to be loaded into any physical memory location - **relocatable object file**
- Linker combines these into single binary **executable** file
- Program resides on secondary storage as binary executable
- Must be brought into memory by **loader** to be executed
	- **Relocation** assigns final addresses to program parts and adjusts code and ata in program to match those addresses
- Modern general purpose systems don't link libraries into executables
	- Rather, **dynamically linked libraries** (DLL in windows) are loaded as needed, shared by all the use the same version of that same library (loaded once)
	- Object, executable files have standard formats, so OS knows how to load and start them
## Why Applications are OS Specific
- Apps compiled on one system usually not exe on other OS
- Each OS provides its own unique syscalls
- Apps can be multi-OS
	- Written in interpreted language and interpreter available on multiple OSs
	- App written in language that includes VM containing the running app
	- Use standard language (like C) compile separately on each OS to run on each
- **Application Binary Interface** (ABI) is architecture equivalent of API, defines how different components of a binary can interface for a given OS on a given architecture, CPU, etc.
## OS Design and Implementation
- **User** goals and **System** goals
	- User goals - OS should be convenient
	- System goals - OS should be easy to design and implement
- Important policy
	- **Policy** - What will be done?
	- **Mechanism** - How to do it?
- Specifying and designing an OS is highly creative task of **software engineering**
### Implementation
- Much variation
	- Early OSes in asm language
	- Then system programming languages like Algol, PL/1
	- Now C, C++
- Actually usually a mix of languages
	- Lowest levels in asm
	- Main body in C
	- Systems programs in C, C++, scripting languages like PERL, Python, shell scripts
- More high-level language easier to **port** to other hardware
	- But slower
- **Emulation** can allow an OS to run on non-native hardware
## OS System Structure
- General-purpose OS is very large program
- Various ways to structure ones
	- Simple - MS-DOS
	- More complex - UNIX
	- Layered - an abstrcation
	- Microkernel - Mach
### Monolithic Structure - OG UNIX
- UNIX - limited by hardware functionality, the OG UNIX OS had limited structuring. The UNIX OS consists of two separable parts
- Systems programs
- The kernel
	- Consists of everything below the syscall interface and above the physical hardware
- Basically one big piece using layers
### Microkernels
- Moves as much from the kernel into user space
- **Mach** example of **microkernel**
	- MacOS X kernel (**Darwin**) partly based on Mach
- Communication takes place between user modules using **message passing**
- Benefits:
	- Easier to extend a microkernel
	- Easier to port the OS to new architectures
	- More reliable (less code is running in kernel mode)
	- More secure
- Detriments
	- Performance overhead of user space to kernel space communication
### Modules
- Many modern OSes implement **loadable kernel modules** (LKMs)
	- Uses OO approach
	- Each core component is separate
	- Each talks to the others over known interfaces
	- Each is loadable as needed within the kernel
- Overall, similar to layers but with more flexibility
	- Linux, Solaris, etc.
### Hybrid Systems
- Most modern OSes are actually not one pure model
	- Hybrid combines multiple approaches to address performance, security, usability needs
	- Linux and Solaris kernels in kernel address space, so monolithic, plus modular for dynamic loading of functionality
	- Windows mostly monolithic, plus microkernel for different subsystem **personalities**
- Apple MacOS X hybrid, layered, Aqua UI plus Cocoa programming environment
	- Below is kernel consisting of Mach microkernel and BSD Unix parts, plus IO kit and dynamically loadable modules (called **kernel extensions**)
- Hybrid systems are essentially monolithic, but without the strict structure of traditional monolithic systems, such as System V.
## Building and Booting an OS
- OSes generally designed to run on a class of systems with variety of perpherals
- Commonly OS already installed on purchased computer
	- But can build and install some other OSes
	- If generating an OS from scratch
		- Write the OS source code
		- Configure the OS for the system on which it will run
		- Compile the OS
		- Install the OS
		- Boot the computer and its new OS
### System Boot
- When power initialized on system, execution starts at a fixed memory location
- OS must be made available to hardware so hardware can start it
	- Small pieces of code - **bootstrap loader**, **BIOS**, stored in **ROM** or **EEPROM** locates the kernel, loads it into memory, and starts it
	- Sometimes two-step process where **boot block** at fixed location loaded by ROM code, which loads boostrap loader from disk
	- Modern systems replace BIOS with **Unified Extensible Firmware Interface (UEFI)**
- Common bootstrap loader, **GRUB**, allows selection of kernel from multiple disks, versions, kernel options
- Kernel loads and system is then **running**
- Boot loaders frequently allow various boot states, such as single user mode
## OS Debugging
- Debugging is finding and fixing bugs, as well as performance tuning
- OS generate **log files** containing error information
- Failure of an application can generate **core dump** file capturing memory of the process
- OS failure can generate **crash dump** file containing kernel memory
- Beyond crashes, performance tuning can optimize sys performance
	- Somtimes using trace listings of activities record for analysis
	- **Profiling** is periodic sampling of IP to look for statitistical trends
	- 