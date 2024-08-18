
**WHAT ?**
**Exception:**  An exception is an unexpected event, that usually arises during the execution of the program. This leads to the disruption to the normal flow of the program and then the program get stops abnormally.

**Exception handling**
An Exception Handling is a technique which helps to retain the normal flow of the program, even if the unexpected problems arise in the code during the execution. Commonly, The problems arise are:

1. Wrong input data formats,
2. Network Connection Failure,
3. Opening a non-existing file and more.

![](https://miro.medium.com/v2/resize:fit:1154/1*33dZ05GU2kKlMVnvhBI8XQ.png)



**Exception hierarchy**:
![[Pasted image 20240619223527.png]]

**Types of exceptions**
![[Pasted image 20240619223603.png]]

**Checked Exceptions:** _An exception that is handled or checked by the compiler at compilation time only. Example are IOException, SQLException, Interrupted Exception, FileNotFoundException, etc._

**Unchecked Exceptions:** _An exception that is handled or checked at the time of execution or runtime only. Example are ArithmeticException, NumberFormat Exception, ArrayIndexOutOfBoundsException, SecurityException, etc._

**Error:** _Errors are irreversible. It always happens at runtime. It is caused by the environment in which the application is running. Example are OutOfMemoryError, AssertionError, etc.


**Built-in exceptions** 
- Un-**Checked Exception**
	- Arithmetic Exception
	- Null pointer Exception
	- NumberFormat Exception
	- IndexOutOfBound Exception
- **Checked Exception**
	- SQL Exception
	- IO Exception
	- ClassNotFound Exception
###### User Defined Exceptions
User Defined Exceptions are the exceptions which are not present in the java exception library. We programmers used to create and use our own designed exceptions in order to enhance the error statements for better understanding.
class HelloWorld{
  public static void main(String args[]){
    try{
    int a = 9;
    int b = 0;
    int c = 10;
    //int e = a / b;
    int f = a / c;
    System.out.println("Result is:" + f);
    if(f == 0){
        throw new MyException("My Designed Exception");
    }
    }
    catch(ArithmeticException e){
        System.out.println("ERROR IN DIVIDING");
    }
    catch(MyException e1){
        System.out.println(e1.getMessage());
    }
  }
}
class MyException extends Exception{
    public MyException(String message){
        super(message);
    }
}



**Exception Handling Keyword**
![[Pasted image 20240619225102.png]]

**Try**
This block is used to specify a block where we should place the exception code.
Syntax:
_try{//Code that throws an exception}_

**Catch**
This block is used to handle the exception.
Syntax:\
_catch(Exception e){// handling of exception}_

**Finally**
This Block is used to specify the important code, which we want to run anyway. Even if an exception arise and not handled using catch block, finally block statements will run, certainly. This block usually include code for closing connections or streams, etc.

**Throw**
This is a keyword used to throw an exception.

**Throws**
This is a keyword used to declare exceptions. It does not throw any exception, but tells that there can be any exception in a method. Always used with the method signature. It gives an information to the programmers that there can be exception.
class HelloWorld{
    static void print() throws NumberFormatException{
        System.out.print("Function1");
        throw new NumberFormatException("HELLO FUNCTION 1");
    }
}

**Exception propogation**
Exception propagation is a concept of transferring the exception from one method to its previous method in order to handle the exception.
![[Pasted image 20240619225336.png]]
In this example, we have taken two methods, m1() and m2(). We have called m2() method in m1() and have raised an exception in m2() method. But we have just raised and exception, but not handled it. So it propagates the exception to the previous method or caller method and now the caller method that is m1() method is responsible for the handling of the exception.


**Error vs Exception**
![[Pasted image 20240619225435.png]]

**Throw vs Throws**
![[Pasted image 20240619225452.png]]