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
C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
    #include <stdio.h>
    #include <unistd.h>

    int main() {
        pid_t pid, ppid;

        pid = getpid();     // Get current process ID
        ppid = getppid();   // Get parent process ID

        printf("Process ID: %d\n", pid);
        printf("Parent Process ID: %d\n", ppid);

        return 0;
    }
```
##OUTPUT

![image](https://github.com/user-attachments/assets/1833a6c7-0f1c-4727-a764-edd573eceab3)

#PROGRAM:

C Program to create new process using Linux API system calls fork() and exit()
```
    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>

    int main() {
        pid_t pid;

        pid = fork();  // Create a new process

        if (pid < 0) {
            // Fork failed
            perror("fork failed");
            exit(1);
        } else if (pid == 0) {
            // Child process
            printf("Child Process:\n");
            printf("  PID: %d\n", getpid());
            printf("  Parent PID: %d\n", getppid());
            exit(0);  // Child exits
        } else {
            // Parent process
            printf("Parent Process:\n");
            printf("  PID: %d\n", getpid());
            printf("  Child PID: %d\n", pid);
            exit(0);  // Parent exits
        }
    }
```
##OUTPUT

![image](https://github.com/user-attachments/assets/faddae11-b487-47f1-9ce5-452898936b75)

## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
```
    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>

    int main() {
        printf("Before executing ls -l\n");

        // execl(path, arg0, arg1, ..., NULL)
        execl("/bin/ls", "ls", "-l", NULL);

        // If execl() is successful, the lines below won't execute
        perror("execl failed");
        exit(1);
    }
```
##OUTPUT

![image](https://github.com/user-attachments/assets/5255bbc4-d529-44e4-9936-e533a462adc9)

# RESULT:
The programs are executed successfully.















