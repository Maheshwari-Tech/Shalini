- It is declared abstract
- It needs to be extended and it cannot be instantiated.
- can have **constructor**, **final method** and **static method**.
- they **may have** or **may not have** method implementation
- If a method is declared abstract then its implementation has to be provided by the class extending the abstract class.
- If you are not providing the implementation for the abstract method while extending, that new class should also be abstract class only.
- We can have **an abstract class without abstract method** as well as they can contain final methods also.
- While extending an abstract class we have to implement all of its abstract method.

**Syntax: –**
public abstract class Automobile {   
	public abstract void engine();   
	public void  gearBoxGearOne(){     
		//method implementation   
	}
}

public class Car extends Automobile {   
	_@Override_   
	public void engine() {     
		//Method implementation  for abstract method.
	}
}