#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <pthread.h>
#include <sys/wait.h>

#define NUM_PROCESSES 2
#define NUM_THREADS 3

void* thread_function(void* arg) {
    int thread_num = *((int*)arg);
    printf("Thread %d: PID = %d, TID = %ld\n", thread_num, getpid(), pthread_self());
    return NULL;
}

void create_threads_in_process() {
    pthread_t threads[NUM_THREADS];
    int thread_args[NUM_THREADS];

    for (int i = 0; i < NUM_THREADS; i++) {
        thread_args[i] = i + 1;
        if (pthread_create(&threads[i], NULL, thread_function, &thread_args[i]) != 0) {
            perror("Failed to create thread");
            exit(EXIT_FAILURE);
        }
    }

    // Wait for all threads to complete
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }
}

int main() {
    pid_t pid;
    for (int i = 0; i < NUM_PROCESSES; i++) {
        pid = fork();
        if (pid < 0) {
            perror("Failed to fork");
            exit(EXIT_FAILURE);
        } else if (pid == 0) {
            // Child process
            printf("Process %d: PID = %d\n", i + 1, getpid());
            create_threads_in_process();
            exit(0);  // Child process should exit after creating threads
        }
    }

    // Parent process waits for all child processes
    for (int i = 0; i < NUM_PROCESSES; i++) {
        wait(NULL);
    }

    return 0;
}
