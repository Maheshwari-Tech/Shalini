
**WHAT ?**
Locking is essential to successful SQL Server transactions processing and it is designed to allow SQL Server to work seamlessly in a multi-user environment. Locking is the way that SQL Server manages transaction concurrency. Essentially, locks are in-memory structures which have owners, types, and the hash of the resource that it should protect. A lock as an in-memory structure is 96 bytes in size.

Locking is like the traffic cop ensuring that chaos doesn’t erupt when multiple threads or users try to read or modify the same piece of data concurrently.

**WHY ?**
To understand better the locking in SQL Server, it is important to understand that locking is designed to ensure the integrity of the data in the database, as it forces every SQL Server transaction to pass the ACID test.

SQL Server locking is the essential part of the isolation requirement and it serves to lock the objects affected by a transaction. While objects are locked, SQL Server will prevent other transactions from making any change of data stored in objects affected by the imposed lock. Once the lock is released by committing the changes or by rolling back changes to initial state, other transactions will be allowed to make required data changes.

**TYPES**
1. **Pessimist**
	Pessimistic locking is a concurrency control mechanism that operates under the premise that data conflicts or inconsistencies are probable when multiple users or processes access the same resource simultaneously.
	
	The main idea behind pessimistic locking is to acquire locks on resources preemptively, maintaining exclusive access to these resources for the entire duration of a transaction or critical operation. By doing so, it prevents other users or processes from accessing or modifying the locked resource until the lock is released.
###### Key Characteristics of Pessimistic Locking:
1. **Acquiring Locks Upfront:** Before performing any read or write operation on a resource, pessimistic locking acquires locks on the resource to prevent other concurrent transactions from accessing it concurrently.
2. **Exclusive Access:** Once a lock is obtained, it grants exclusive access to the locked resource to the transaction that holds the lock. Other transactions must wait until the lock is released before they can access the resource.
3. **Potential for Waiting:** Since locks are held for the entire duration of a transaction, there might be waiting times for other transactions if they request access to the locked resource.
4. **Different Granularities:** Pessimistic locking can operate at various granularities, such as database-level locks, table-level locks, row-level locks, or even finer-grained locks at the column level.
###### ✅ Pros
- Ensures data consistency by preventing concurrent modifications that could lead to inconsistencies.
- Straightforward approach to managing concurrent access.

###### ❌ **Cons**
- Potential for increased contention and waiting times, especially in scenarios with high concurrency.
- Locks held for extended periods might impact system performance and throughput.

**Understanding Pessimistic Locking with an example**
Assume we have a counter and multiple threads are trying to increment this counter concurrently.

**With Pessimistic Locking**

import java.util.concurrent.locks.ReentrantLock;  
  
public class CounterWithLock {  
    private static int counter = 0;  
    private static final ReentrantLock lock = new ReentrantLock();  
  
    public static void main(String[] args) throws InterruptedException {  
        Thread[] threads = new Thread[100000];  
  
        for (int i = 0; i < 100000; i++) {  
            threads[i] = new Thread(() -> {  
                lock.lock();  
                try {  
                    counter++;  
                } finally {  
                    lock.unlock();  
                }  
            });  
              
            threads[i].start();  
        }  
  
        for (Thread thread : threads) {  
            thread.join();  
        }  
  
        System.out.println("Counter with lock (pessimistic locking): " + counter);  
    }  
}

In this scenario, we expect the result to be **100000** and it is indeed **100000**.

###### When to use Pessimistic Locking
- **High Contention:** In scenarios where conflicts are frequent or expected, such as in banking systems handling critical transactions, pessimistic locking might be more suitable. It ensures exclusive access to resources, reducing the chance of conflicts and maintaining data integrity.
- **Long Transactions:** When transactions hold locks for extended periods due to complex operations or user interactions, pessimistic locking can prevent inconsistencies by keeping resources locked until the transaction completes.


2. **OPTIMIST**
	Optimistic locking is a concurrency control mechanism used in computer systems, particularly in databases, to manage concurrent access to shared resources with an optimistic assumption that conflicts are infrequent or less likely to occur.

 **Key Concepts of Optimistic locking**
1. **Validation Before Commit:** Rather than preventing concurrent access, optimistic locking defers conflict detection until the time of committing changes. It allows transactions to proceed independently and optimistically assumes that conflicts won’t arise during the execution phase.
2. **Validation at Commit Time:** Before committing changes, the system checks whether any other transaction has modified the resource since the current transaction started. This validation is typically done by comparing versions or timestamps associated with the resource.
3. **Handling Conflicts:** If conflicts are detected during the validation phase (e.g., if another transaction modified the resource), the system takes appropriate action. This could involve rolling back the current transaction or retrying it to incorporate the latest changes.
###### ✅ **Pros**
- Reduced contention: Allows concurrent access without blocking, potentially improving system concurrency.
- Minimal locking overhead: Transactions proceed independently, reducing the need for acquiring and managing locks.

###### ❌ **Cons**
- Increased chances of conflicts: Might require retrying transactions or handling conflicts, leading to additional logic and complexity.
- Not suitable for highly contended resources: In scenarios with frequent conflicts, optimistic locking might not be the most efficient approach.

**Understanding Optimistic Locking with an example**
We will take the same example again and see how we can achieve the same behavior with optimistic locking.

**With Optimistic Locking**

import java.util.concurrent.atomic.AtomicInteger;  
  
public class OptimisticLockingExample {  
    private static AtomicInteger counter = new AtomicInteger(0);  
    private static int version = 0;  
  
    public static void main(String[] args) throws InterruptedException {  
        int numThreads = 100000;  
        Thread[] threads = new Thread[numThreads];  
  
        for (int i = 0; i < numThreads; i++) {  
            threads[i] = new Thread(() -> {  
                int localCounter;  
                  
                do {  
                    localCounter = counter.get(); // Get the current counter value  
  
                // Compare-and-swap operation  
                } while (!counter.compareAndSet(localCounter, localCounter + 1));  
            });  
  
            threads[i].start();  
        }  
  
        for (Thread thread : threads) {  
            thread.join();  
        }  
  
        System.out.println("Counter value after optimistic locking: " + counter);  
    }  
}

The `AtomicInteger` named `counter` is used to represent the shared variable that multiple threads will attempt to increment. If the compare-and-swap operation fails due to a version change by another thread, the loop continues until the update succeeds.

###### When to use Optimistic Locking
- **Low Contention:** In scenarios where conflicts are rare or infrequent, such as in read-heavy systems or non-critical data operations, optimistic locking can be more suitable. It allows concurrent access without blocking, potentially improving system concurrency.
- **Short Transactions:** When transactions are short-lived and the likelihood of conflicts is minimal, optimistic locking’s non-blocking nature can be beneficial, as it avoids unnecessary waiting times.