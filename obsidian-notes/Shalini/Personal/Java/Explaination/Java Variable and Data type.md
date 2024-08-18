###### **Java Variable**
A variable is a container which holds the value while the [Java program](https://www.javatpoint.com/simple-program-of-java) is executed. A variable is assigned with a data type.
Variable is a name of memory location. There are three types of variables in java: local, instance and static.
There are two types of [data types in Java](https://www.javatpoint.com/java-data-types): primitive and non-primitive.
![variables in java](https://static.javatpoint.com/core/images/variable.png)

![types of variables in java](https://static.javatpoint.com/core/images/types-of-variables1.png)

#### 1) Local Variable

A variable declared inside the body of the method is called local variable. You can use this variable only within that method and the other methods in the class aren't even aware that the variable exists.

A local variable cannot be defined with "static" keyword.

#### 2) Instance Variable

A variable declared inside the class but outside the body of the method, is called an instance variable. It is not declared as [static](https://www.javatpoint.com/static-keyword-in-java).

It is called an instance variable because its value is instance-specific and is not shared among instances.

#### 3) Static variable

A variable that is declared as static is called a static variable. It cannot be local. You can create a single copy of the static variable and share it among all the instances of the class. Memory allocation for static variables happens only once when the class is loaded in the memory.


###### **Java Data Types**

Data types specify the different sizes and values that can be stored in the variable. There are two types of data types in Java:

1. **Primitive data types:** The primitive data types include boolean, char, byte, short, int, long, float and double.
2. **Non-primitive data types:** The non-primitive data types include [Classes](https://www.javatpoint.com/object-and-class-in-java), [Interfaces](https://www.javatpoint.com/interface-in-java), and [Arrays](https://www.javatpoint.com/array-in-java).

## Java Primitive Data Types

In Java language, primitive data types are the building blocks of data manipulation. These are the most basic data types available in [Java language](https://www.javatpoint.com/java-tutorial).

![Java Data Types](https://static.javatpoint.com/images/java-data-types.png)

|**Data Type**|**Default Value**|**Default size**|
|---|---|---|
|boolean|false|1 bit|
|char|'\u0000'|2 byte|
|byte|0|1 byte|
|short|0|2 byte|
|int|0|4 byte|
|long|0L|8 byte|
|float|0.0f|4 byte|
|double|0.0d|8 byte|
