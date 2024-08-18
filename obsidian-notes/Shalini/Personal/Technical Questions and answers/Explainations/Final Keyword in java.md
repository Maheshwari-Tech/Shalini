
**WHAT ?**
The final keyword is used to indicate that a variable, method, or class cannot be modified or extended. Here are some of its characteristics: Final variables: When a variable is declared as final, its value cannot be changed once it has been initialized

**WHY ?**
In Java, the final keyword is used to indicate that a variable, method, or class cannot be modified or extended.

- **Final variables:** When a variable is declared as final, its value cannot be changed once it has been initialized. This is useful for declaring constants or other values that should not be modified. Again we cannot assign value to the already declared variable.
- **Final methods**: When a method is declared as final, it cannot be overridden by a subclass. This is useful for methods that are part of a class’s public API and should not be modified by subclasses.
- **Final classes:** When a class is declared as final, it cannot be extended by a subclass. This is useful for classes that are intended to be used and should not be modified or extended.

**USE CASE**
1. **Final Variable :**
When a variable is declared with the **_final keyword_**, its value can’t be modified, essentially, a constant. This also means that you must initialize a final variable. It is good practice to represent final variables in all uppercase, using underscore to separate words.

Example:-
1) final int THRESHOLD = 5; //Final variable
2) final int THRESHOLD; //Blank final variable
3) static final double PI = 3.141592653589793; //Final static variable PI
4) static final double PI; //Blank final static variable

2. **Final Methods :**
When a method is declared with _final_ keyword, it is called a final method. A final method cannot be Overridden. We must declare methods with the final keyword for which we are required to follow the same implementation throughout all the derived classes.

Example:- //we cannot override the final method in derived class.

class A  
{  
final void m1()  
{  
System.out.println(“This is a final method.”);  
}  
}

class B extends A  
{  
void m1()  
{  
// Compile-error! We can not override  
System.out.println(“Illegal!”);  
}  
}

3. **Final Classes :**

When a class is declared with _final_ keyword, it is called a final class. A final class cannot be extended(inherited).

Example: //We cannot inherit or extend Final class.

final class A  
{  
// methods and fields  
}  
// The following class is illegal  
class B extends A  
{  
// COMPILE-ERROR! Can’t subclass A  
}