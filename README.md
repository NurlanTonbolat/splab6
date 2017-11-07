# Lab6 - pthread debugged with helgrind

This lab is the homework of [Chapter 27, Interlude : Thread API](http://pages.cs.wisc.edu/~remzi/OSTEP/threads-api.pdf)  
The code can be found [here](http://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html)  
Format your answers neatly and submit.

### Q1
```
$ valgrind --tool=helgrind man-race
...

```
---
1. __What information does helgrind give to you?__  
_`helgrind` says `Possible data race during read of size 4 at 0x602094 by thread #1 ... at 0x400CC3: main (main-race.c:15)`
and `This conflicts with a previous write of size 4 by thread #2 ... at 0x400C7D: worker (main-race.c:8)`_
2. __Does it point to the right lines of code?__  
_Approximately._

### Q2

### Q3

### ...

### Q9
