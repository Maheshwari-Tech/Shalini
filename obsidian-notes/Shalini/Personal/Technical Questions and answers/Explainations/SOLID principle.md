**WHAT ?**
**S** - Single Responsibility Principle
**O** - Open closed Principle
**L** - Liskov substitution Principle
**I** - Interface Segregation
**D** - Dependency Inversion

1. **Single Responsibility Principle**
	![[Pasted image 20240617235255.png]]


- Class should have a single responsibility.
- If a Class has many responsibilities, it increases the possibility of bugs because making changes to one of its responsibilities, could affect the other ones without you knowing.
- This principle aims to separate behaviours so that if bugs arise as a result of your change, it won’t affect other unrelated behaviours.
EG: 
- Open a database connection
- Fetch data from database
- Write the data in an external file

2. **OPEN CLOSED PRINCIPLE**
![[Pasted image 20240617235652.png]]
- Classes should be open for extension but closed for modification.
- Changing the current behaviour of a Class will affect all the systems using that Class.
- If you want the Class to perform more functions, the ideal approach is to add to the functions that already exist NOT change them.
- This principle aims to extend a Class’s behaviour without changing the existing behaviour of that Class. This is to avoid causing bugs wherever the Class is being used.
EG:
- This principle aims to extend a Class’s behaviour without changing the existing behaviour of that Class. This is to avoid causing bugs wherever the Class is being used.

3. **Liskov Substitution Principle**
 ![[Pasted image 20240618184000.png]]
 - If S is a subtype of T, then objects of type T in a program may be replaced with objects of type S without altering any of the desirable properties of that program.
 - The **child** Class should be able to process the same requests and deliver the same result as the **parent** Class or it could deliver a result that is of the same type.
 - This principle aims to enforce consistency so that the parent Class or its child Class can be used in the same way without any errors.

4. **Interface Segregation Principle** :
 ![[Pasted image 20240618185205.png]]
 - Clients should not be forced to depend on methods that they do not use.
 - A Class should perform only actions that are needed to fulfil its role. Any other action should be removed completely or moved somewhere else if it might be used by another Class in the future.
 - This principle aims at splitting a set of actions into smaller sets so that a Class executes ONLY the set of actions it requires.

5. **Dependency Inversion Principle**:
![[Pasted image 20240618190422.png]]
  - High-level modules should not depend on low-level modules. Both should depend on the abstraction.
  - Abstractions should not depend on details. Details should depend on abstractions.
  - This principle says a Class should not be fused with the tool it uses to execute an action. Rather, it should be fused to the interface that will allow the tool to connect to the Class.
  - It also says that both the Class and the interface should not know how the tool works. However, the tool needs to meet the specification of the interface.

EG:
 - Notification Manager -> INotificationSender ----> SMSSender.
									 ----> WhatsAppSender.
									 ----> EmailSender.
