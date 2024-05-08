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

## C Program to print process ID and parent Process ID using Linux API system calls

```

// C Program to print process ID and parent Process ID using Linux API syatem calls
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return id of calling function
	process_id=getpid();
	//getppid() - will return process id of parent function
	p_process_id=getppid();
	//printing the process ids
//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of the parent function: %d\n",p_process_id);
	return 0;}

```










##OUTPUT
![image](https://github.com/VasanthiSivasankar/Linux-Process-API-fork-wait-exec/assets/161431945/4f9924c5-a115-4d3b-b3da-2a352be828c2)














## C Program to create new process using Linux API system calls fork() and exit()

```
//C Program to create new process using Linux API system calls fork() and exit()
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
int main()
{
    int pid;
    pid=fork();
    if (pid==0)
    {
        printf("Iam child, my pid is %d\n",getpid());
        printf("My parent pid is : %d\n",getppid());
        exit(0);
    }
    else{
        printf("I am parent, my pid is %d\n",getpid());
        sleep(100);
        exit(0);
    }
}









```
##OUTPUT

![image](https://github.com/VasanthiSivasankar/Linux-Process-API-fork-wait-exec/assets/161431945/d3e9f533-97a3-4561-8b13-fb6c967ebd7d)







## C Program to execute Linux system commands using Linux API system calls exec() family

```
//C Program to execute Linux system commands using Linux API system calls exec() family
#include <stdlib.h>
#include <stdio.h>
#include <sys/wait.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
    int status;
    printf("Running ps with execlp\n");
    execl("ps","ps","ax",NULL);
    wait(&status);
    if (WIFEXITED(status))
        printf("child exited with the status of %d\n",WEXITSTATUS(status));
    else    
        puts("child did not exit succesfully\n");
    printf("Done.\n");
    exit(0);
}






















```
##OUTPUT

![image](https://github.com/VasanthiSivasankar/Linux-Process-API-fork-wait-exec/assets/161431945/e73b5e0f-e479-4594-a04e-3d457d8b7dc6)

















# RESULT:
The programs are executed successfully.
