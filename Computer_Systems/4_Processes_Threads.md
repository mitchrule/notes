## Processes

### The Process Model

In this model, all runnable software on the computer, including the operating
system, is organised into processes. A process is just an instance of an executing
program, including all of it's current registers and variables.

Conceptually, each process has its own virtual CPU, but this is not the case. In
reality the CPU switches back and forth between processes, executing one at any
given time. It is much easier to think of this as a collection of processes running
in pseudo-parallel. This concept is called _multiprogramming_.

#### Process Creation

There are four principle events that can cause processes to be created:

1. System initialisation.
2. Execution of a process creation system call by a running process.
3. A user request to create a new process.
4. Initiation of a batch job

Processes that stay running in the background, to do things such as check for
incoming emails or print queues, are called _daemons_. Large systems typically
have dozens of them.

In UNIX there is only one system call to create a new process: `fork`. This call
creates an exact clone of the calling process. After the fork, the two processes
have the same memory image, the same environment strings, and the same open files.

Usually the child process then executes `execve` or a similar system call to change
its memory image and run a new program. For example, when a user types a command
`sort`, the shell forks off a child process and the child executes `sort`. This is
so the child process can manipulate its file descriptors after the fork but before
execve in order to accomplish redirection of standard input, output, and error.

After a process is created, the parent and child each have their own distinct
address space. Changes are not visible between processes.

#### Process Termination

There are four principle events that can cause a process to be terminated:

1. Normal exit (voluntary)
2. Error exit (voluntary)
3. Fatal error (involuntary)
4. Killed by another process (involuntary)

Most processes terminate because they have done their work.

The second reason is if the process discovers a fatal error, for example, a file
does not exist. The program exits and prompts the user as to why the program exited.

The third reason is due to an error caused by the process, such as a bug in the code.

The final reason a process may terminate is that a process executes a system call to
kill the process. The called must have the necessary authorisation to kill the killee.

#### Process Hierarchies

When a process creates another process, the two processes can continue to be
associated in certain ways. The child can create more processes, forming a
hierarchy.

In UNIX, a process and all of its children and further descendants form a process
group. When the user sends a signal from the keyboard, the signal is delivered
to all members of the process group currently associated with the keyboard. Each
process has the choice to catch the signal, ignore it, or take the default action,
which is to be killed by the signal.

When a UNIX system boots, a special process called `init` is started. It reads a
file telling it how many terminals there are, and forks off a new process for each
terminal. These processes wait for someone to login, then executes a shell to accept
commands. These commands can then start even more processes. This forms a single
process tree, with `init` at the root.

#### Process States

Although each process is an independent entity, processes often need to interact
with other processes.

If a process is ready but must wait for another process to finish executing, it
must block until some input is available.

A process may be in one of three states at any given time:

1. RUnning (actually using CPU at that moment)
2. Ready (runnable, temporarily stopped to let another process run)
3. Blocked (unable to run until some external event happens)

In UNIX, when a process reads from a pipe or special file and there is no input
available, it is automatically blocked.

#### Implementation of Processes

The operating system maintains a table called the process table. This table
contains important information about each process' state, including its program
counter, stack pointer, memory allocation, the status of its open files, and everything
else about the process that must be saved when the process is switched from running
to ready or blocked so that it can be restarted later.
