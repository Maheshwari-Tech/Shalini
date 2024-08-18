**WHAT ?**
- Polymorphism is the ability of an object to take on many forms.
- The child class object can be assigned to any class reference in its parent hierarchy and of course itself as well.

Eg: Lets say Student class is a child of Person class
Student student = new Student()  
Person person = new Student() //upcasting
The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. 

There are 2 types of polymorphism which are commonly mentioned.

1. Dynamic Polymorphism
2. Static Polymorphism

1. **Dynamic Polymorphism** (Method Overrideing)
	This is also mentioned as **Run-Time polymorphism, Dynamic binding, Run-Time binding, Late binding and Method overriding.** Here having many forms is happening in different classes.
	
class Person {      
   public void teach(){  
      System.out.println("Person can teach");  
   }  
}  
  
class Teacher extends Person {  
   public void teach() {  
      System.out.println("Teacher can teach in a school");  
   }  
}  
  
public class TestTeacher {  
   public static void main(String args[]) {  
      Person person = new Person(); //Person reference and object  
      Person another_person = new Teacher(); //Person reference, Teacher object  
      Teacher teacher = new Teacher(); //Teacher reference and obj.      person.teach();//output: Person can teach      // Here you can see Teacher object's method is executed even-  
      // -though the Person reference was used    
      another_person.teach();//output: Teacher can teach in a school      teacher.teach();//output: Teacher can teach in a school  
   }  
}


2. **Static polymorphism** (Method Overloading)
	This is also mentioned as **Compile-Time polymorphism, Static binding, Compile-Time binding, Early binding and Method overloading.** Here having many forms is happening in the same class.
	
	**But Java doesn’t support the Operator Overloading.**
	When there are multiple functions with the same name but different parameters then these functions are said to be ****overloaded****. Functions can be overloaded by changes in the number of arguments or/and a change in the type of arguments.
	class Calculator {  
	    void add(int a, int b) {  
	         System.out.println(a+b);  
	    }  
	    void add(int a, int b, int c) {  
	         System.out.println(a+b+c);  
	    }  
	}
	public class Demo {  
	   public static void main(String args[]) {  
	       Calculator calculator = new Calculator();       // method with 2 parameters is called  
	       calculator.add(10, 20); //output: 30       // method with 3 parameters is called  
	       calculator.add(10, 20, 30); //output: 60  
	   }  
	}