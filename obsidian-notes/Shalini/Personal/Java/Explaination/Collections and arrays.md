**Arrays** - 
1. int a[]={33,3,4,5};//declaration, instantiation and initialization
2. For each loop - 
	- /Java Program to print the array elements using for-each loop  
	- class Testarray1{  
	- public static void main(String args[]){  
	- int arr[]={33,3,4,5};  
	- //printing array using for-each loop  
	- for(int i:arr)  
	- System.out.println(i);  
	- }}
3.    passing array to method  - 
	-  //Java Program to demonstrate the way of passing an array  
	- //to method.  
	- class Testarray2{  
	- //creating a method which receives an array as a parameter  
	- static void min(int arr[]){  
	- int min=arr[0];  
	- for(int i=1;i<arr.length;i++)  
	-  if(min>arr[i])  
	-   min=arr[i];  
	
	- System.out.println(min);  
	- }  
	
	- public static void main(String args[]){  
	- int a[]={33,3,4,5};//declaring and initializing an array  
	- min(a);//passing array to method  
	- }}
4.  Anonymous Array in Java
	- 1. /Java Program to demonstrate the way of passing an anonymous array  
	- //to method.  
	- public class TestAnonymousArray{  
	- //creating a method which receives an array as a parameter  
	- static void printArray(int arr[]){  
	- for(int i=0;i<arr.length;i++)  
	- System.out.println(arr[i]);  
	- }  

	- public static void main(String args[]){  
	- printArray(new int[]{10,22,44,66});//passing anonymous array to method  
	- }}
5.  int carr[]=arr.clone();