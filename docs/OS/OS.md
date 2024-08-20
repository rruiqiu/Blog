## Pipe

A pipe is a small kernel buffer exposed to processes as a pair of file descriptors, one for reading and one for writing. Writing data to one end of the pipe makes that data available for reading from the other end of the pipe. *<u>**Pipes provide a way for processes to communicate.**</u>*

Pipe is a shared resource(file descriptor) that allows two process to interchange data with each other, fork() won't create a duplicate of the pipe.





## Fork (Process)

fork(), 

A process may create a new process using the fork system call. Fork gives the new process exactly the same memory contents (both instructions and data) as the calling process. ***<u>Fork returns in both the original and new processes. In the original process, fork returns the new process’s PID. In the new process, fork returns zero. The original and new processes are often called the parent and child.</u>***

```c
int pid = fork();
if(pid > 0){
    printf("parent: child=%d\n", pid);
    pid = wait((int *) 0);
    printf("child %d is done\n", pid);
} else if(pid == 0){
    printf("child: exiting\n");
    exit(0);
} else {
    printf("fork error\n");
}
```

### wait

The wait system call returns the PID of an exited (or killed) child of the current process and copies the exit status of the child to the address passed to wait; if none of the caller’s children has exited, `wait` waits for one to do so. If the caller has no children, `wait` immediately returns -1. If the parent doesn’t care about the exit status of a child, it can pass a 0 address to wait.

Short Summary:  For this code below, the `wait` will wait until child completes and it will store the child exit status into the `&status` which is a user-defined variable, the wait will return the child process ID which store in the `terminate_pid` below.

`pid_t terminated_pid = wait(&status); // Wait for child to terminate`



## Pipe and Xargs in Unix

**Input Handling**:

- **Pipe (`|`)**: Directly connects the output of one command to the input of another.
- **`xargs`**: Reads input from stdin and converts it into command-line arguments for another command.

**Command Compatibility**:

- **Pipe (`|`)**: Best used when the receiving command can process input from stdin.
- **`xargs`**: Useful when the receiving command does not read from stdin but instead requires command-line arguments.

**Flexibility**:

- **Pipe (`|`)**: Simpler and more straightforward for linear data flow.
- **`xargs`**: Offers more flexibility with options to handle arguments, such as `-n` (number of arguments per command line), `-I` (replace string), and `-0` (null-terminated input).

### Summary

- **Pipe (`|`)**: Use when you want to **<u>*pass the output of one command directly as input to another command that reads from stdin*</u>**.
- **`xargs`**: Use when you need to <u>***convert input from stdin into command-line arguments for a command that does not read from stdin.***</u>



[here](https://ruiqiu.netlify.app/AEVdemo)





