## Linux-Process-API-fork-wait-exec-
## Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise

## AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

## DESIGN STEPS:
Step 1:
Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

Step 2:
Write the C Program using Linux Process API - fork(), wait(), exec()

Step 3:
Test the C Program for the desired output.

## PROGRAM:
C Program to print process ID and parent Process ID using Linux API system calls
#include <stdio.h>

#include <sys/types.h>

#include <unistd.h>

int main(void)

{ //variable to store calling function's process id

pid_t process_id;

//variable to store parent function's process id

pid_t p_process_id;

//getpid() - will return process id of calling function

process_id = getpid();

//getppid() - will return process id of parent function

p_process_id = getppid();

//printing the process ids//printing the process ids

printf("The process id: %d\n",process_id);

printf("The process id of parent function: %d\n",p_process_id);

return 0; }
## OUTPUT

<img width="854" height="62" alt="319454984-d24beae3-3302-41af-881e-30172c3510e1" src="https://github.com/user-attachments/assets/c995df10-8dd2-4dfe-961c-a1e8bf6dad68" />


## C Program to create new process using Linux API system calls fork() and exit()
#include <stdio.h>

#include<stdlib.h>

int main()

{ int pid;

pid=fork();

if(pid == 0)

{ printf("Iam child my pid is %d\n",getpid());

printf("My parent pid is:%d\n",getppid());

exit(0); }

else{

printf("I am parent, my pid is %d\n",getpid());

sleep(100);

exit(0);}

}

## OUTPUT

<img width="855" height="57" alt="319455100-b1cd969c-4bc1-43dc-8f87-abf8ff6b2f90" src="https://github.com/user-attachments/assets/96d9d616-eb8a-4f15-804a-7fd2d6a2bec2" />


## C Program to execute Linux system commands using Linux API system calls exec() family
#include <unistd.h>

#include <stdio.h>

#include <stdlib.h>

#include <sys/wait.h>

#include <sys/types.h>

int main()

{ int status;

    printf("Running ps with execlp\n");
    
    execl("ps", "ps", "ax", NULL);
    
    wait(&status);
    
    if (WIFEXITED(status))
    
            printf("child exited with status of %d\n", WEXITSTATUS(status));
            
    else
    
            puts("child did not exit successfully\n");
            
    printf("Done.\n");

    printf("Running ps with execlp. Now with path specified\n");
    
    execl("/bin/ps", "ps", "ax", NULL);
    
    wait(&status);
    
    if (WIFEXITED(status))
    
            printf("child exited with status of %d\n", WEXITSTATUS(status));
            
    else
    
            puts("child did not exit successfully\n");
            
    printf("Done.\n");
    
    exit(0);}
## OUTPUT


<img width="855" height="193" alt="319455196-98132d53-20dd-4faa-bf2e-54d7196c174e" src="https://github.com/user-attachments/assets/5bba4fd9-c585-45a7-bdce-9e45dc5f429e" />


## RESULT:
The programs are executed successfully.


