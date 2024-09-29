# Multi-Process and Multi-Thread Program

This program demonstrates the creation of multiple processes and threads in a Linux environment using the `fork()` and `pthread` libraries in C. Each process creates a set number of threads, and each thread prints its Process ID (PID) and Thread ID (TID).

## Code Overview

- The program defines two constants: 
  - `NUM_PROCESSES` (set to 2): The number of processes to be created.
  - `NUM_THREADS` (set to 3): The number of threads to be created within each process.
  
- The main function creates `NUM_PROCESSES` processes using `fork()`.
  - Each child process calls the function `create_threads_in_process()` to create `NUM_THREADS` threads using `pthread_create()`.
  
- Each thread, when created, prints:
  - Its corresponding thread number.
  - The Process ID (PID) of the process in which it is running.
  - The Thread ID (TID) using `pthread_self()`.

- The parent process waits for all child processes to complete using `wait()`.

### Thread Function

The function `thread_function(void* arg)` is the function executed by each thread. It prints:
  - The thread number passed as an argument.
  - The process ID (PID) of the process in which the thread is running.
  - The thread ID (TID) returned by `pthread_self()`.

### Process Creation

In the `main()` function:
1. The program creates `NUM_PROCESSES` child processes using `fork()`.
2. Each child process runs the `create_threads_in_process()` function, creating multiple threads.
3. After thread creation, each child process exits.

### Thread Creation

The function `create_threads_in_process()`:
1. Creates `NUM_THREADS` using `pthread_create()`.
2. Each thread runs the `thread_function()`.
3. The function waits for all threads to finish using `pthread_join()` before returning.

## How to Compile

To compile the code, use the following command:

```bash
gcc -o multi_process_thread multi_process_thread.c -lpthread
