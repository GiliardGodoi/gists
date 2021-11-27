# How to handle with process

## Monitoring with htop

```shell
htop
```

1. [How to use htop command to monitor system processes in real time](https://www.fosslinux.com/18444/how-to-use-htop-command-to-monitor-system-processes-in-real-time.htm)
2. [Command htop explanation](https://linuxtogether.org/htop-command-explanation/)


## Monitoring with ps

Listing processes

    ps -aux

To list the output in Linux's format:

    ps -e

or

    ps -A

To get more information:

    ps -f

or to get more information than before:

    ps -F

To list an user's processes:

    ps -u username

To list an user's attached processes:

    ps -x

To list a group related processes:

    ps -g groupname

To know what are the group names try: `less\etc\group`

To list processes related to an executavel:

    ps -C chrome

To list processes related to a terminal:

    ps -t pts\0

Show processes' hierarchy:

    ps -eH

To list and sort by cpu or memory usage:

    ps -eo pid,ppid,cmd,%mem,%cpu --sort=%cpu | head
    ps -eo pid,ppid,cmd,%mem,%cpu --sort=%mem | head

or

    ps -aux --sort=%cpu | head

To list not respondent ones:

    ps -A | grep -i stress

## Others useful commands

    nice

It keeps a command running even if the session is disconnected or the user logs out.

    nohup

https://www.computerhope.com/unix/unice.htm

https://www.journaldev.com/27875/nohup-command-in-linux

It limits the cpu usage

    cpulimit

## Finishing processes

    kill PID

