 Multi-Process and Multi-Thread code

This simple C code demonstrates process and thread creation using POSIX `fork()` and `pthread` libraries.The program spawns multiple processes, with each process creating several threads, which print their Process ID (PID) and Thread ID (TID).

 Features

Creates **multiple processes** using `fork()`.
Each process spawns **multiple threads** using `pthread_create()`.
Threads print their unique **PID** and **TID**.


To compile and run this program, you need linux or a UNIX operating system:
GCC compiler
POSIX threads (pthread) library

 Cloning the Repository

git clone https://github.com/Paul-ms-dot/Demo-code

cd <repository-directory>

to compile

  gcc -o multi_process_thread multi_process_thread.c -lpthread

to run

  multi_process_thread
