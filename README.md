# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls


#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid;
    pid = fork();

    if (pid < 0) {
        printf("Fork failed.\n");
        return 1;
    }
    else if (pid == 0) {
        printf("Child Process:\n");
        printf("My PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    }
    else {
        printf("Parent Process:\n");
        printf("My PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
    }

    return 0;
}










## OUTPUT


<img width="655" height="208" alt="512060489-afd72057-6519-4f32-bbe7-1d3044b1d2ef" src="https://github.com/user-attachments/assets/7d7cdf38-8f1f-4115-8e7c-b06c6e9870b2" />






## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family






#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t pid;
    pid = fork();

    if (pid < 0) {
        printf("Fork failed.\n");
        return 1;
    }
    else if (pid == 0) {
        printf("Child process executing 'ls -l' command...\n");
        execl("/bin/ls", "ls", "-l", NULL);
        printf("execl() failed.\n"); // Only executes if exec fails
    }
    else {
        wait(NULL);
        printf("Child process finished execution.\n");
        printf("Parent process exiting.\n");
    }

    return 0;
}




















## OUTPUT











<img width="987" height="492" alt="512062617-c6dfe1ea-1402-4124-83f8-7069ed33de86" src="https://github.com/user-attachments/assets/7bc1baed-97e0-48c6-bd9a-60257cee5f72" />







# RESULT:
The programs are executed successfully.
