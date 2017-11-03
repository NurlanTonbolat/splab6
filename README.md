# Lab6 - pthread debugged with helgrind

This lab is the homework of [Chapter 27, Interlude : Thread API](http://pages.cs.wisc.edu/~remzi/OSTEP/threads-api.pdf)  
The code can be found [here](http://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html)  
Format your answers neatly and submit.


### Q1
```C
#include <stdio.h>

#include "mythreads.h"

int balance = 0;

void* worker(void* arg) {
    balance++; // unprotected access 
    return NULL;
}

int main(int argc, char *argv[]) {
    pthread_t p;
    Pthread_create(&p, NULL, worker, NULL);
    balance++; // unprotected access
    Pthread_join(p, NULL);
    return 0;
}
```

```
$ valgrind --tool=helgrind man-race
...

```
---
__1. What information does helgrind give to you?__  
_Well..._

### Q2

### Q3

### ...

### Q9
