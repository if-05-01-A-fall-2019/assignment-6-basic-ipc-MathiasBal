# Basics

## Race Condition
A race condition is basically about two processes which try to be the last to be called.

## Disabling Interrupts
### i)
If you were to disable interupts on one core the other cores would still be able to access the shared memory.
### ii)
It is possible that the user just might forget to enable interupts again.

## Peterson Solutoin
