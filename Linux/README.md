## Problem description
Assume there are three types of threads in the system, A, B, and C.
There is buffer with size of 1 between A and B, where A writes data into the buffer and B reads data from the buffer;
and another buffer of size 1 between B and C,
where B writes the data read from the first buffer into this one, and C reads the data from it.

Here, the implememted system is with 1) busy waiting sync mechanism 2) semaphore. 

## To build these files
```
g++ main.c -lpthread -o run-me
g++ main_busy_waiting.c -lpthread -o run-me-2
```

## How to run
After you build it, navigate to where the file main.c/run is located and run
```
./run-me
./run-me-2 # run the other one after you stop this one by interrupting it with Ctrl + C
```

## Program overview
Here are two kind of implementation of the chained producer&consumer problem, 
busy-waiting and non-busy-waiting (semaphore) implementations.    

N_LOOP is defined to decide when to stop the infinite loop, in other words, it keeps producing and consuming until C has
consumed N_LOOP times.    

Elapsed times(in nanosecond) when process C has consumed for i times is stored in the csv files, 
statistics_non-busy-waiting.csv and statistics_busy-waiting.csv respectively, where i is from 1 to N_LOOP. We are able
to run the executable file for as many times as we want to compare the performance between these two implementation.  

## Sample standard output
Use "Ctrl + C" to stop(interrupt) the program.
```
Process A is writing A into buffer1
Process B is reading A from buffer1
Process A is writing A into buffer1
Process B is writing A into buffer2
Process B is reading A from buffer1
Process C is reading A from buffer2
Process A is writing A into buffer1
Process B is writing A into buffer2
Process B is reading A from buffer1
Process C is reading A from buffer2
...
```

