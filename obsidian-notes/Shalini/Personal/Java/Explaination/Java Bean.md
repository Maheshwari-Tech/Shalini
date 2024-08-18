**WHAT**
A JavaBean is a Java class that should follow the following conventions:- 
It should have a no-arg constructor.
- It should be Serializable.
- It should provide methods to set and get the values of the properties, known as getter and setter methods.

**WHY**
According to Java white paper, it is a reusable software component. A bean encapsulates many objects into one object so that we can access this object from multiple places. Moreover, it provides easy maintenance.

## Simple example of JavaBean class

1. //Employee.java  

3. package mypack;  
4. public class Employee implements java.io.Serializable{  
5. private int id;  
6. private String name;  
7. public Employee(){}  
8. public void setId(int id){this.id=id;}  
9. public int getId(){return id;}  
10. public void setName(String name){this.name=name;}  
11. public String getName(){return name;}  
12. }

## How to access the JavaBean class?

To access the JavaBean class, we should use getter and setter methods.

1. package mypack;  
2. public class Test{  
3. public static void main(String args[]){  
4. Employee e=new Employee();//object is created  
5. e.setName("Arjun");//setting value to the object  
6. System.out.println(e.getName());  
7. }}

A JavaBean property may be read, write, read-only, or write-only. JavaBean features are accessed through two methods in the JavaBean's implementation class:

**1. getPropertyName ()**

For example, if the property name is firstName, the method name would be getFirstName() to read that property. This method is called the accessor.

**2. setPropertyName ()**

For example, if the property name is firstName, the method name would be setFirstName() to write that property. This method is called the mutator.

### Advantages of JavaBean

The following are the advantages of JavaBean:
- The JavaBean properties and methods can be exposed to another application.
- It provides an easiness to reuse the software components.

### Disadvantages of JavaBean

The following are the disadvantages of JavaBean:

- JavaBeans are mutable. So, it can't take advantages of immutable objects.
- Creating the setter and getter method for each property separately may lead to the boilerplate code.



https://medium.com/@tcf01/spring-what-is-bean-and-why-does-it-matter-907d126a3b08