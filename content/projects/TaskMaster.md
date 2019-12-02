Title: Taskmaster
Date: 2019-11-29 23:14
Modified: 2019-11-29 23:21
Category: Python
Tags: Python, 42
Slug: TaskMaster
Authors: Abraham Gimbao, Marc Jose
Summary: It is a question of creating a job control program, in the language of your choice. What you will be asked to accomplish is very close to the supervisor program.

Your program must be able to start jobs like child processes, let them "live" and restart them if necessary. He must also know to any time if these processes are alive or dead.
Information on which program to launch, how, how much, if they should be launched restart, etc.... must be contained in a configuration file. You have the choice of format (YAML may be a good idea but it is up to you). This configuration must be started at startup and must be reloadable while taskmaster is turning by sending him a SIGHUP. When it has recharged, your program must apply the changes to its current state (delete programs, add programs, change their control conditions, etc.), but it must NOT delete processes that have not changed with reloading. Your program must have a system of registers to record events in a local file (When a program starts, stops, restarts, when it dies unexpectedly, when the configuration is updated, etc.). Once your program is launched it must remain active in the background and give access to a shell to the user. It MUST not be a shell in its own right like the 42sh, but it must at least have basic functionalities such as line editing, history, etc... self-completion would also be nice. Get inspired by the supervisor shell, supervisorctl.

This shell must at least allow the user to:

    - See the status of all the programs described in the configuration file (with the "status" command).

    - Start / stop / restart programs.

    - Reload the configuration file without the main program stopping.

    - Stop the main program.

The configuration file must allow the user to specify the following in order to each program must be supervised:

    - The command to use to launch the program.

    - The number of processes to start and run.

    - Choose to launch this program at startup or not.

    - Choose whether the program should always be restarted, never, or only when it stops unexpectedly.

    - Which return code represents an "expected" output of the program.

    - How long does the program have to run after it starts for it is considered that he has "launched himself correctly".

    - How many times must a restart be performed before stopping.

    - Which signal should be used to stop (i.e. exit gracefully) the program.

    - How many waiting times after a graceful stop before killing the program.

    - Options to remove stdout/stderr from the program or to redirect to files.

    - Set environment variables before running the program.

    - A working directory a set before starting the program.

    - A umask a set before running the program.
