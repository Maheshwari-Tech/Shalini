
Correctness and optimality.

**Ensuring correctness : locking and atomic instance.**
**Ensuring optimality : Fairness, efficient logic**

Locking - mutex, semaphore, atomic instances, syncronise keyword.

Counting prime numbers till 100 million - 
- Sequential approach - [4m10s]
- Add Threads - [1m]
	- 10 threads each handling on equal range of 10 million
	- We did speed up but was it fair?
		- Smaller number can be checked quickly 1 to srqt(n).
		- more prime number in smaller range
	- Some threads finish early and wait for others to complete.
- Threading with fairness - [51s]
	- 10 threads, each thread picks up the next unprocessed unmber and check if it is prime.
	- Global variable currentNum
	- each thread
		- increment current number atomically
		- check prime
	- All threads end at nearly same time and do nearly the same work - maximize optimality.