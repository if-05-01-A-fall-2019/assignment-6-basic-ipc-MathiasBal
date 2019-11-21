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
#### Scenario 1
+ The first process enters the critical region.
+ The second process is blocked from entering the critical region.
+ The first process does whatever it has to do.
+ The second process still has to wait for the first process to leave.
+ The first process is finished and leaves the critical region.
+ The second process enters the critical region.
#### Scenario 2
+ The first and second process enter a loop almost at the same time.
+ The loser gets stuck in a loop while the other process gets to work.
+ The working process finishes and leaves the region.
+ The loser can leave the loop and work.

### ii) Play through the scenario which makes the strict alternation approach fail. Document how it fails.
Basically one process (A) with a big time slice might get to go through 8 lines in one run while the other process (B) might only get 2 lines per run.
+ A sees that turn != 0 so it can continue and doesn't get stuck in the loop.
+ A goes through the 7 following lines.
+ A enters the critical region and changes turn to 1.
+ A executes the noncritical region.
+ A looks if turn != 0 4 times which leaves it in a loop.
+ B sees that turn != 1 so it can continue and doesn't get stuck in the loop.
+ B enters the critical region.
+ B already ran through 2 lines.
+ A can't leave the loop since turn = 1, but it has to see 8 times.
+ B leaves the critical region and changes turn to 0.

### iii) What is the meaning of the variable loser in Peterson's solution? When does it have any effect?
The loser is the second process which tries to enter the critical region which it can't since it is blocked off by the winner.

#### iv) Extend the given functions such they can handle three processes.
int winner;
bool isInterested[3];
 
int getProccess(int process, int number){
  int ret = process -number;
  if(ret == -1){
    return 2;
  }
  if(ret == -2){
    return 1;
  }
  return ret;
} 

void leave_region(int process){
  isInterested[process] = false;
  winner=getPRocess(winner, 1);
  isInterested[winner] = true;
}

void enter_region(int process){
  int otherOne = getProccess(procces,1);
  int otherTwo = getProccess(process,2);
  winner = process;
  isInterested[winner] = true;
  while (winner != process && interested[winner]) ;
}
