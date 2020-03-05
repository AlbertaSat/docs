# Assignment 1

1. Goals:
Make use of several multithreading pthread calls. Introduce multitasking, synchronistion, and resource protection and sharing. Also some vague notion of how some components of an embedded power system might actually be programmed.
The actual satellite is using an operating system called FreeRTOS. Doing a quick (and suggested) google search, you will find that FreeRTOS is a popular option for projects such as ours. It is a powerful, lightweight Real Time Operating System made for microcontrollers such as our Cortex-R5F microcontroller.
FreeRTOS provides a very similar API for threading, tasks, and synchronization as POSIX. Hence for this excericise we will use the POSIX pthreads API to get some points across.
It is suggested to begin by reading about multithreading, thread safety and learn the proper usage of these powerful operating system features, both in POSIX, and in FreeRTOS (see the resource section for suggested starting points).