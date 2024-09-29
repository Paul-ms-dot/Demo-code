 Multi-Process and Multi-Thread Program

This C program demonstrates process and thread creation using POSIX `fork()` and `pthread` libraries. The program spawns multiple processes, with each process creating several threads, which print their Process ID (PID) and Thread ID (TID).

 Features

- Creates **multiple processes** using `fork()`.
- Each process spawns **multiple threads** using `pthread_create()`.
- Threads print their unique **PID** and **TID**.


To compile and run this program, you need a Linux or Unix-like operating system with the following:
- GCC compiler
- POSIX threads (pthread) library

 Cloning the Repository

```bash
git clone <repository-url>
cd <repository-directory>

to compile
  gcc -o multi_process_thread multi_process_thread.c -lpthread

to run
  multi_process_thread
