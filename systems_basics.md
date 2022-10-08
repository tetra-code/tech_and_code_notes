# Basics

## Shell
A shell is a computer program, specifically a *Command-line Interpreter*, that acts as an interface between the kernel and the computer program. It exposes the OS's services to the user or other programs. It is considered the outermost layer around the operating system, hence the name shell. It uses either a *Command-line Interface* or *Graphical User Interface* 

Each OS have their own unique shell. The *Windows shell* is a GUI with readily identifiable elements consisting of the desktop, the taskbar, the Start menu, the task switcher and the AutoPlay feature. 
These elements are called *shell objects* and there is a shell object hierarchy, with the 'Desktop' being at the top of the hierarchy. Recycle Bin, Libraries, Control Panel, This PC and Network are examples of such shell objects. 

## Kernel
The Kernel is a very low-level computer program at the core of the OS. It operates purely inside the OS and generally has complete control over everythin in the system. It is the primary interface between the OS and underlying computer hardware. The kernel connects these two in order to adjust resources as effectively as possible. 

This is where shell comes in; it is an interface between the kernel and the user (computer program)

Simply put, it does all the jobs requested by a higher level program.

![image](../../images/kernel_shell_app.png)

## Emulator
An *emulator* is either a hardware or software that allows a computer (here called the *host*) to immitate the behaviors of another computer (here called the *guest*). This allows the host system to run software originally desigend for the guest device.

Many printers, for example, are desigend to emulate HP LaserJet printers because so much software is written specifically for HP printers. A non-HP printer will emulate a HP printer and this allows the HP-printer-specific software to also run on the non-HP printer. Another example is video game enthusiasts using emulators to emulate old video game consoles to play classic arcade games on modern video game consoles.

## Terminal
A *computer terminal* is a hardware device that you use to interact with the computer system. The simplest actions are entering data and extract data from the computer. Thus a display monitor, keyboard, mouse are all considered a terminal. Nowadays most display monitors are *graphics terminals*, meaning they are capable of displaying graphics in addition to (or instead of ) test-only displays like old computer displays.

### Terminal window
The terminal window allows the user to acces the text terminal and all its applications like the CLI and TUI applications.

### Terminal emulator
The *terminal emulator* or *terminal application* is a computer program that emulates a video terminal within some other display architecture. A terminal is a text input and output environment. A terminal window, also known as a terminal emulator, is a text-only window that emulates a console in a graphical user interface (GUI). In other words, a graphical user interface application from which we can access a user's console.29 

## Bash
While bash is primarily the shell for Unix and Linux, a version is also available for Windows 10 via the *Windows Subsystem for LInux*, allowing bash users to manipulate the windows OS with bash.

Bash is an important language to be good at, especially if you're doing systems or network related. Even if you are not using bash or the command line on a regular basis, it is still a good skill to have. Benefits include:

- Most servers run on a Linux distro, which communicates mainly with the bash shell. 
- Command Line Skills Help With Building Repeatable Data Processes. The command line is well suited for data is acquired, processed and displayed in the same way because commands are easily automated and replicated.
- You will also have more flexibility if you can use the terminal rather than having to rely on clicking through GUIs.
- Cloud services often are connected to and operated through a command line interface.
- Unix Shell Skills Transfer Well to Other Shells
- Get work done faster: You Can Probably Type Faster Than You Click
- Auditing and Debugging is Easier

## Unix
Its most common shell is *bash*. Techinically it can run many different shells on top of its kernel but *bash*just happens to be the most common one.