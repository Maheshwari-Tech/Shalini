**WHAT and WHY?**
- Blue print of a class.
- **Static, constant and abstract methods** allowed.
- It only has the empty methods and not the implementation.
- **IS-A** relationship.
- It **cannot be instantiated.**
- Used to achieve **loose coupling**
- All the fields are **public, static and final by default**.
- A class that implements interface **must implement all the methods declare in the interface**.
- use **implements** keyword to implement the interface.
- In case the class does not provide an implementation for all the methods of the interface then the class must be declared abstract.
- They provide total abstraction.
- They help to achieve what we call multiple inheritances as java doesn’t support multiple inheritances, but you can implement several interfaces in one class and thus it helps to achieve multiple inheritance.
- 

**Syntax:**
public interface TelevisionRemote {  
	public void turnOnTelevision();
		public void turnOffTelevision();
	}
}

public class Television implements TelevisionRemote {   
	_@Override_   
	public void turnOnTelevision() {   
		//method implementation details   
	}   
	_@Override_   
	public  void turnOffTelevision() {   
		//method implementation details   
	}
}