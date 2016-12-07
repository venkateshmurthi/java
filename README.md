# java
Linux command to print memory usage of the Process

pmap - report memory map of a process

Printing the memory usage of the Java Process.

echo 0 $(awk '/TYPE/ {print "+", $2}' /proc/`pidof PROCESS`/smaps) | bc
Where "PROCESS" is the name of the process you want to inspect and "TYPE" is one of:

Rss: resident memory usage, all memory the process uses, :1
including all memory this process shares with other processes. It does not include swap;
Shared: memory that this process shares with other processes;
Private: private memory used by this process, you can look for memory leaks here;
Swap: swap memory used by the process;
Pss: Proportional Set Size, a good overall memory indicator. It is the Rss adjusted for sharing: if a process has 1MiB private and 20MiB shared between other 10 processes, Pss is 1 + 20/10 = 3MiB
