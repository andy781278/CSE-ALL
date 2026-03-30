used after fork, waits until child process finishes

int status;
wait(&status);

blocks the caller until **any** child terminates
returns the pid of the finished child
fills in status with information about how it ended

waitpid(pid,&status,0) - waits for a specific child

if (WIFEXITED(status)) {
    int code = WEXITSTATUS(status);
}

true of child exited normally, gives exit code 0-255

if (WIFSIGNALED(status)) {
    int sig = WTERMSIG(status);
}

true of child killed by a signal, WTERMSIG gives signal