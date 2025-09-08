#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid;

    pid = fork();

    if (pid < 0) {
        perror("Fork failed");
        return 1;
    } 
    else if (pid == 0) {
        sleep(5);
        printf("Child: I am orphan now. My PID = %d, My new Parent PID = %d\n",
               getpid(), getppid());
    } 
    else {
        printf("Parent: Exiting immediately. My PID = %d, Child PID = %d\n",
               getpid(), pid);
    }

    return 0;
}
