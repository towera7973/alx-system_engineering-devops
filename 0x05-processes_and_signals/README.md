0x05. Processes and signals
What is a process & PID ?
In computing, PID stands for "Process ID" or "Process Identifier." It is a unique numerical identifier assigned to each running process in an operating system. A process is an executing instance of a program, and the PID allows the operating system to keep track of and manage these processes effectively.

When a program or application is executed, the operating system creates a new process for it, and this process is given a unique PID. The PID serves as a reference that the operating system uses to identify and interact with the specific process. It's like an address that the operating system uses to locate and manage the resources associated with that process.

PID values are typically positive integers, and they can range from 1 to a certain maximum value, depending on the operating system. The PID 1 is typically reserved for the system's init process (or its successor, like systemd on some modern systems), which is the first process started during the boot process and acts as the parent process of all other processes.

PID usage is crucial for various system tasks, such as process control, monitoring, and termination. For example, when you want to stop or kill a specific process, you use its PID to target the correct process for termination. System administrators and developers often use tools and commands to monitor and manage processes by referencing their PIDs.

How to find a process’ PID ?
We can use various commands and tools depending on your operating system. Here are some common methods for different platforms:

Unix-like systems (Linux, macOS, etc.):

pgrep command: It allows you to find the PID of a process based on its name.

pgrep process_name
The -l flag in the pgrep command stands for "list" or "long format." When you use the -l flag with pgrep, the command not only outputs the Process IDs (PIDs) of the matched processes but also includes the process names (COMMAND) along with their PIDs.

Here's the syntax of the pgrep command with the -l flag:

pgrep -l <pattern>
pgrep -f "some_command"
pgrep -f : -f flag :will search for the process whose full command-line contains "some_command" and return its PID.
”without the -f flag, it searches for the exact process name, not the entire command-line pattern.”

pgrep -l versus pgrep -f outputs:
pgrep -l "command"

pgrep -f "command"

ps command “Process Status”: It shows information about running processes, including their PIDs.

ps -ef | grep process_name
-ef option is used to display a detailed list of all running processes on a Unix-like operating system. It is commonly used on Linux and macOS systems.

Here's the breakdown of each flag in the -ef option:

-e: Selects all processes. This option ensures that all processes running on the system are listed, not just those associated with the current terminal session.

-f: Displays a full format listing. This option provides more detailed information about each process, including the process hierarchy (parent-child relationship), resource utilization, and other attributes.

pidof command:

It is used to find the PID of a running program by name.

pidof process_name

To find the process name, you can use various commands and tools depending on your operating system. Here are some common methods for different platforms:

Unix-like systems (Linux, macOS, etc.):

ps command: It shows information about running processes, including their names. ps -ef top command: It provides real-time information about running processes, including their names.

top


What is a signal ?
In computing, a signal is a software interrupt delivered to a process or a thread by the operating system. It is a mechanism used to notify a process about events or requests that require its attention or action. Signals are an essential part of inter-process communication and process management in operating systems.

Process Termination: Signals can be used to request the termination of a process gracefully. For example, the SIGTERM signal is commonly used to ask a process to exit cleanly, allowing it to perform any necessary cleanup before shutting down.

Forced Termination: The SIGKILL signal is used to forcefully terminate a process without allowing it to perform any cleanup. This signal is often used when a process becomes unresponsive or needs to be stopped immediately.

Process Synchronization: Signals can be used to synchronize the activities of different processes or threads. For example, the SIGUSR1 and SIGUSR2 signals are user-defined signals that can be used for specific synchronization purposes.

Error Handling: Some signals are generated when a process encounters errors or exceptional conditions. For example, the SIGSEGV signal is generated when a process attempts to access an invalid memory address.

Alarm and Timeouts: The SIGALRM signal can be used to set alarms or timers to notify a process after a specified amount of time has passed.

Different operating systems have their own sets of predefined signals, and developers can also create their custom signals for specific needs. Signal handling is an important aspect of writing robust and responsive applications, allowing them to respond to various events and conditions effectively.

What are the 2 signals that cannot be ignored
In Unix-like operating systems, there are two signals that cannot be ignored by a process: `SIGKILL` and `SIGSTOP`. These signals have a fixed behavior that cannot be overridden or handled by the process, ensuring certain critical functionality of the operating system.


It's important to exercise caution when using these signals, especially `SIGKILL`, as abruptly terminating a process may result in data corruption or leave system resources in an inconsistent state. Generally, it is recommended to first attempt to terminate a process gracefully using the `SIGTERM` signal (Signal number 15) before resorting to `SIGKILL`.

pkill - kill
pkill: uses process name

Explanation: pkill is used to send a signal to a process or processes based on their name.

Example: Terminate all processes with the name "myprocess."

pkill myprocess
kill: uses PID

Explanation: kill is used to send a signal to a process using its PID.

Example: Send the SIGTERM signal to process with PID 1234 to terminate it gracefully.

kill 1234
trap

Example: Trap SIGTERM to perform cleanup before exiting a script

Suppose you have a script that performs some operations and you want to ensure that certain cleanup actions are taken before the script exits, regardless of how it terminates. You can use a trap to catch the SIGTERM signal (sent when you use the kill command with PID) and perform cleanup before the script exits.


The trap command is used to set up the trap that calls the cleanup function when the SIGTERM signal is received.
Type your email...
Subscribe
Foreground processes & background processes
Foreground processes interact with the user directly, and the user must wait for them to finish before they can continue using the terminal.

For example, if you run a command like ls, cat, or gcc in the terminal, these commands will be executed as foreground processes, and the terminal will wait for their completion before accepting new commands.

Background processes run independently of the terminal, and the user can continue using the terminal while they are running. They are often started by appending & to the command when executing it.

sleep 60 &

proc
One of the primary purposes of /proc is to provide information about running processes. Each process running on the system has a directory inside /proc with its PID as the directory name. For example, /proc/1234/ represents the directory for process with PID 1234.

It's important to note that the files in the /proc directory are not real files, but rather pointers to kernel data structures and system information. As such, attempting to modify the contents of a /proc file can have unintended consequences and is generally not recommended.

Hints for practice:
The output of the ps command, which displays information about running processes. Let's break down each part of the output:


PID 2659: It is a Bash shell process (bash) running in the terminal (pts/4).

PID 15020: It is the ps command itself that was used to display the information about running processes.

ps command with the -efH options .The -e option ensures that all processes are listed, including those not associated with a terminal (TTY). The -f option provides a full format listing, and the -H option shows the process hierarchy in a tree-like structure.

TTY is a terminal or text-based interface that allows users to interact with a computer system, execute commands, and receive text-based output.
when you execute a command in the terminal, the command's output is sent to the TTY, and the command can read user input from the TTY. Additionally, if a process running in the foreground requires user interaction (e.g., input from the keyboard), it will read that input from the TTY.
Other flags of ps :
-a: Selects all processes. This option ensures that all processes running on the system are listed, not just those associated with the current terminal session.

-u: Displays a user-oriented format. This option provides additional information including the username, which started the process.

-x: Includes processes without a controlling terminal (TTY). This option lists both foreground and background processes.

-f: Displays a full format listing. This option provides more detailed information about each process, including the process hierarchy (parent-child relationship), resource utilization, and other attributes.

sleep is a command-line utility found in Unix-like operating systems, including Linux and macOS. It is used to create a time delay or pause in the execution of a script or command. When you run the sleep command, it suspends the execution for the specified amount of time, allowing you to introduce a waiting period in a script or shell command.

The syntax of the sleep command is simple:

sleep <duration>  
sleep 5
Resources :

Digital Ocean Commands for Process Management in Linux

This is an updating content…


