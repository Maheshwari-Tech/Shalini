
**WHAT ?**
![[Pasted image 20240617173525.png]]

ACID is an acronym that stands for **Atomicity, Consistency, Isolation**, and **Durability**. These properties collectively define the characteristics that guarantee the reliability of database transactions.

**WHY ?**
1. ***ATOMICITY*** :
	Atomicity ensures that a transaction is treated as a single, indivisible unit of work. Either all the changes made by the transaction are committed to the database, or none of them are. In the event of a failure or error during the transaction, the system ensures that the database remains unchanged.
	
	**Problem**: Imagine a banking system where a transfer involves deducting money from one account and adding it to another. If the deduction succeeds but the addition fails, the system would be left in an inconsistent state.
	
	**Solution**: Atomicity ensures that a transaction is treated as a single, indivisible unit of work. It either completes entirely or not at all, preventing partial updates.
	
	**Example**:
	BEGIN TRANSACTION;  
	UPDATE Accounts  
	SET Balance = Balance - 1000  
	WHERE AccountID = 1;  
	UPDATE Accounts  
	SET Balance = Balance + 1000  
	WHERE AccountID = 2;  
	COMMIT;
	
	In this example, the two `UPDATE` statements are wrapped in a transaction. If either update fails, the entire transaction is rolled back, maintaining data consistency.
	
2. ***CONSISTENCY*** :
	Consistency guarantees that a transaction brings the database from one valid state to another. If the database is consistent before a transaction starts, it will remain consistent after the transaction is completed. Any violation of integrity constraints will result in the transaction being rolled back.

	**Problem**: Consider an e-commerce system with a rule that the total stock of a product must match the sum of stock across all warehouses. If an update violates this rule, the system would be inconsistent.

	**Solution**: Consistency ensures that a transaction brings the database from one valid state to another, honoring all defined rules and constraints.
	
	**Example**:
	CREATE FUNCTION CheckStockConsistency()  
	RETURNS INT  
	AS  
	BEGIN  
	    IF (SELECT SUM(Stock) FROM Warehouses) != (SELECT TotalStock FROM Products)  
	        RETURN 0;  
	    RETURN 1;  
	END;  
	ALTER TABLE Warehouses  
	ADD CONSTRAINT CK_StockConsistency  
	CHECK (dbo.CheckStockConsistency() = 1);
	
	Here, we define a consistency rule using a user-defined function and a check constraint. The constraint ensures that the total stock in the `Products` table always matches the sum of stock across all `Warehouses`.
	
3. ***ISOLATION*** :
    Isolation ensures that multiple transactions can execute concurrently without interfering with each other. Each transaction appears as if it is executed in isolation, even though it may be running concurrently with other transactions. This prevents data corruption and ensures that each transaction sees a consistent snapshot of the database.
    
	**Problem**: In a multi-user environment, concurrent transactions may read or modify the same data, leading to anomalies like dirty reads, non-repeatable reads, or phantom reads.
	
	**Solution**: Isolation ensures that concurrent transactions do not interfere with each other, providing appropriate levels of visibility and locks.
	
	**Example**:
	
	SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;  
	BEGIN TRANSACTION;  
	SELECT * FROM Orders WHERE Status = 'Pending';    
	-- Process the orders...  
	UPDATE Orders  
	SET Status = 'Processed'  
	WHERE Status = 'Pending';  
	COMMIT;
	
	By setting the isolation level to `SERIALIZABLE`, we ensure that the transaction has an exclusive lock on the selected rows, preventing other transactions from modifying or reading uncommitted changes.

4. ***Durability*** :
	Durability guarantees that once a transaction is committed, its effects persist even in the face of system failures. The changes made by the transaction are permanently stored in the database and survive subsequent system crashes or restarts.
	
	**Problem**: In case of a system failure, committed transactions must persist  and survive crashes or power outages.
	
	**Solution**: Durability ensures that once a transaction is committed, its changes  are permanently stored in the database and can survive any subsequent failures.
	
	**Example**:
	BEGIN TRANSACTION;    
	INSERT INTO Customers (Name, Email)  
	VALUES ('John Doe', 'john@example.com');  
	COMMIT;  
	-- Safely shut down the database server  
	SHUTDOWN WITH NOWAIT;
	
	By committing the transaction, we ensure that the newly inserted customer record is durably stored on disk and will persist even if the database server is shut down immediately after.


**Challenges and Considerations:**

While ACID properties provide robust guarantees, they may come with trade-offs in terms of system performance and scalability. In certain scenarios, databases may choose to relax ACID constraints to achieve higher throughput, as seen in NoSQL databases.