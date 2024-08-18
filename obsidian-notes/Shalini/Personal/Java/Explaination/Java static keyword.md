The **static keyword** in [Java](https://www.javatpoint.com/java-tutorial) is used for memory management mainly. We can apply static keyword with [variables](https://www.javatpoint.com/java-variables), methods, blocks and [nested classes](https://www.javatpoint.com/java-inner-class). The static keyword belongs to the class than an instance of the class.

The static can be:

1. Variable (also known as a class variable)
2. Method (also known as a class method)
3. Block
4. Nested class

## Java static variable

If you declare any variable as static, it is known as a static variable.

ADVERTISEMENT

- The static variable can be used to refer to the common property of all objects (which is not unique for each object), for example, the company name of employees, college name of students, etc.
- The static variable gets memory only once in the class area at the time of class loading.

### Advantages of static variable

It makes your program **memory efficient** (i.e., it saves memory).

#### Understanding the problem without static variable

1. class Student{  
2.      int rollno;  
3.      String name;  
4.      String college="ITS";  
5. }  

Suppose there are 500 students in my college, now all instance data members will get memory each time when the object is created. All students have its unique rollno and name, so instance data member is good in such case. Here, "college" refers to the common property of all [objects](https://www.javatpoint.com/object-and-class-in-java). If we make it static, this field will get the memory only once.


## Java static method

If you apply static keyword with any method, it is known as static method.

- A static method belongs to the class rather than the object of a class.
- A static method can be invoked without the need for creating an instance of a class.
- A static method can access static data member and can change the value of it.

### Example of static method

1. //Java Program to demonstrate the use of a static method.  
2. class Student{  
3.      int rollno;  
4.      String name;  
5.      static String college = "ITS";  
6.      //static method to change the value of static variable  
7.      static void change(){  
8.      college = "BBDIT";  
9.      }  
10.      //constructor to initialize the variable  
11.      Student(int r, String n){  
12.      rollno = r;  
13.      name = n;  
14.      }  
15.      //method to display values  
16.      void display(){System.out.println(rollno+" "+name+" "+college);}  
17. }  
18. //Test class to create and display the values of object  
19. public class TestStaticMethod{  
20.     public static void main(String args[]){  
21.     Student.change();//calling change method  
22.     //creating objects  
23.     Student s1 = new Student(111,"Karan");  
24.     Student s2 = new Student(222,"Aryan");  
25.     Student s3 = new Student(333,"Sonoo");  
26.     //calling display method  
27.     s1.display();  
28.     s2.display();  
29.     s3.display();  
30.     }  
31. }  

Output:111 Karan BBDIT
       222 Aryan BBDIT
       333 Sonoo BBDIT
       
There are two main restrictions for the static method. They are:

1. The static method can not use non static data member or call non-static method directly.
2. this and super cannot be used in static context.

### Why is the Java main method static?

Ans) It is because the object is not required to call a static method. If it were a non-static method, [JVM](https://www.javatpoint.com/jvm-java-virtual-machine) creates an object first then call main() method that will lead the problem of extra memory allocation.

## Java static block

- Is used to initialize the static data member.
- It is executed before the main method at the time of classloading.

1. class A2{  
2.   static{System.out.println("static block is invoked");}  
3.   public static void main(String args[]){  
4.    System.out.println("Hello main");  
5.   }  
6. }

