# Basics

## Race Condition
A race condition is basically about two processes which try to be the last to be called so that they don't get overwritten by the other process.

## Disabling Interrupts
### i) Why is it impossible to achieve Mutual Exclusion via disabling interrupts on a multi-core machine?
If you were to disable interupts on one core the other cores would still be able to access the shared memory.
### ii) Why is it dangerous to give user processes the power to disable interrupts?
It is possible that the user just might forget to enable interupts again.

## Peterson Solutoin
### i) Play through the two scenarios of the handout of Peterson's solution. Document how it works.
+ 
