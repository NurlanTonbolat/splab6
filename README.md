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
3. __What other information does it give to you?__  
_It says that `balance` variable is involved in race condition and it says a lot of strange info that I have difficulties to parse._

### Q2
1. __What happens when you remove one of the offending lines of code?__  
`helgrind` does not complain to anything.
2. __Now add a lock around one of the updates to the shared variable, and then around both. What does helgrind report in each of these cases?__  
_With 1 lock `valgrind` complains, whereas with 2 lock `valgrind` does not complain._

### Q3
Now let’s look at main-deadlock.c.  Examine the code.  This code has a problem known as deadlock (which we discuss in much
more depth in a forthcoming chapter). __Can you see what problem it might have?__  
_it is difficult to say from valgrind output what was the problem, but we believe it was deadlock._

### ...

### Q9
