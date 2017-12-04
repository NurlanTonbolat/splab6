# Lab6 - pthread debugged with helgrind

This lab is the homework of [Chapter 27, Interlude : Thread API](http://pages.cs.wisc.edu/~remzi/OSTEP/threads-api.pdf)  
The code can be found [here](http://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html)  
Format your answers neatly and submit.

# Lab6 - pthread debugged with helgrind
This lab is the homework of [Chapter 27, Interlude : Thread API](http://pages.cs.wisc.edu/~remzi/OSTEP/threads-api.pdf) 
The code can be found [here](http://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homewo..)
$Format your answers neatly and submit.

### Q1
valgrind —tool=helgrind ./main-race.c
==26468== Helgrind, a thread error detector
==26468== Copyright (C) 2007-2015, and GNU GPL'd, by OpenWorks LLP et al.
==26468== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==26468== Command: ./main-race.c
==26468==
./main-race.c: 6: ./main-race.c: int: not found
./main-race.c: 8: ./main-race.c: pthread_mutex_t: not found
./main-race.c: 10: ./main-race.c: Syntax error: "(" unexpected
==26468==
==26468== For counts of detected and suppressed errors, rerun with: -v
==26468== Use —history-level=approx or =none to gain increased speed, at
==26468== the cost of reduced accuracy of conflicting-access information
==26468== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
...

—-
1. What information does helgrind give to you?
This reports a warning identifying the data race as well as:

the lines of code in each thread that dangerously access shared memory
the symbol name of the shared memory (balance)
the line of code where the thread is a created

### Q3
—-
There's a potential deadlock if the threads grab their first lock at the same time (i.e. thread 0 grabs lock 1 and thread 1 grabs lock 2, leaving both stuck waiting for the lock they don't have).
### Q4
valgrind —tool=helgrind ./main-deadlock.c
==28042== Helgrind, a thread error detector
==28042== Copyright (C) 2007-2015, and GNU GPL'd, by OpenWorks LLP et al.
==28042== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==28042== Command: ./main-deadlock.c
==28042==
./main-deadlock.c: 5: ./main-deadlock.c: pthread_mutex_t: not found
./main-deadlock.c: 6: ./main-deadlock.c: pthread_mutex_t: not found
./main-deadlock.c: 8: ./main-deadlock.c: Syntax error: "(" unexpected
==28042==
==28042== For counts of detected and suppressed errors, rerun with: -v
==28042== Use —history-level=approx or =none to gain increased speed, at
==28042== the cost of reduced accuracy of conflicting-access information
==28042== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

### Q6
—-
The parent spin waits, checking the value of done until it changes. This wastes processor time that could be used by another process (or even the worker thread if the scheduler is trying to schedule both threads onto the same processor).
### Q7
valgrind —tool=helgrind ./main-signal.c
==28113== Helgrind, a thread error detector
==28113== Copyright (C) 2007-2015, and GNU GPL'd, by OpenWorks LLP et al.
==28113== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==28113== Command: ./main-signal.c
==28113==
./main-signal.c: 5: ./main-signal.c: int: not found
./main-signal.c: 7: ./main-signal.c: Syntax error: "(" unexpected
==28113==
==28113== For counts of detected and suppressed errors, rerun with: -v
==28113== Use —history-level=approx or =none to gain increased speed, at
==28113== the cost of reduced accuracy of conflicting-access information
==28113== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

—-

### Q8
`
valgrind —tool=helgrind ./main-signal-cv.c
==28124== Helgrind, a thread error detector
==28124== Copyright (C) 2007-2015, and GNU GPL'd, by OpenWorks LLP et al.
==28124== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==28124== Command: ./main-signal-cv.c
==28124==
./main-signal-cv.c: 5: ./main-signal-cv.c: //: Permission denied
==28125==
==28125== For counts of detected and suppressed errors, rerun with: -v
==28125== Use —history-level=approx or =none to gain increased speed, at
==28125== the cost of reduced accuracy of conflicting-access information
==28125== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
./main-signal-cv.c: 6: ./main-signal-cv.c: //: Permission denied
==28126==
==28126== For counts
