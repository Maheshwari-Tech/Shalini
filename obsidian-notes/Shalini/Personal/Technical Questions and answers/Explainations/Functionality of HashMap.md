**WHAT ?**
HashMap is a way to assign a unique code for any object after applying a formula and offers an O(1) insertion and retrieval time.

**HOW ?**
###### So how does HashMap internally work?
HashMap uses HashTable implementation internally and consists of two important data structures which are **LinkedList and Array**. **There is a bucket of arrays with each element representing an individual LinkedList**. The Inner Node class consists of a hash value, key, value, and the link to the next Node: 

![[Pasted image 20240618192133.png]]

**How does HashMap know where to store the value in a bucket?**
- To store the values, HashMap uses a concept known as Hashing.
- Hashing is performed using a hashCode() function that converts an Object into HashCode. Based on the hash index results, a slot in the bucket is selected, and the value results are stored.
- As you might think, there would be multiple objects which get hashed to the same bucket index. This is known as **Collision**, and therefore we use a **LinkedList** to store the values which are linked with each other. This can be seen in the representation below.
![[Pasted image 20240619195018.png]]

- A collision occurs when two different values hash to the same bucket index. Let’s consider an example that two integers “1000” and “500” gives us two hash values 100 and 50 respectively. If we consider the total array size as 10, both of them end up in the same bucket i.e. 100 % 10 and 50 % 10). What chaining does is whenever you call the function map.get( “100” );, you are able to retrieve the correct value associated with the key. To verify, we can also utilize the equals method in HashMap.
- You can also override this hashcode function and provide your own implementation. A good hash function is one which distributes the objects evenly.


**EXAMPLE**: 
![[Pasted image 20240619195408.png]]

- **Fetch the data for key sachin:**

map.get(new Key("sachin"));

- ****Steps:**** 
    1. Calculate hash code of Key {“sachin”}. It will be generated as 115.
    2. Calculate index by using index method it will be 3.
    3. Go to index 3 of the array and compare the first element’s key with the given key. If both are equals then return the value, otherwise, check for the next element if it exists.
    4. In our case, it is found as the first element and the returned value is 30.
- Fetch the data for key vaibhav: 

map.get(new Key("vaibhav"));

- ****Steps:**** 
    1. Calculate hash code of Key {“vaibhav”}. It will be generated as 118.
    2. Calculate index by using index method it will be 6.
    3. Go to index 6 of the array and compare the first element’s key with the given key. If both are equals then return the value, otherwise, check for the next element if it exists.
    4. In our case, it is not found as the first element and the next node object is not null.
    5. If the next node is null then return null.
    6. If the next of node is not null traverse to the second element and repeat process 3 until the key is not found or next is not null.
    7. Time complexity is almost constant for the put and the get method until rehashing is not done.
    8. In case of collision, i.e. index of two or more nodes are the same, nodes are joined by a link list i.e. the second node is referenced by the first node and the third by the second, and so on.
    9. If the key given already exist in HashMap, the value is replaced with the new value.
    10. hash code of the null key is 0.
    11. When getting an object with its key, the linked list is traversed until the key matches or null is found on the next field.
    
###### Changes in the Java 8 implementation:

To improve the working of HashMap, Java 8 made updates to the internal implementation workflow. Once a certain threshold level is reached, the values are now automatically stored in a tree manner rather than a linked list. So instead of O(n) retrieval time, we now have better O(log n) retrieval performance. Java only does this when there is a performance gain. This can be seen in the representation below.

In real life, the time complexity of HashMap is not O(1). It is Big O(average size of the collision structure) and is known as amortized O(1).

True O(1) is only achieved by collision-less hashing(also known as “perfect” hashing).

###### Difference between TreeMap, HashMap, LinkedHashMap, and HashTable in Java:

The important distinction is between the ordering and time complexity of the retrieval of data.

**_HashMap:_**

- HashMap offers O(1) insertion and retrieval time.
- It contains value based on keys.
- The ordering of keys is random
- It uses a linked list to store the data.
- It contains only unique elements
- It may have one null key and multiple null values
- It is not thread-safe

**_LinkedHashMap:_**

- LinkedHashMap is the same as HashMap but maintains the insertion order.
- The other properties align with that of HashMap.

**_TreeMap:_**

- TreeMap offers O(log N) insertion and retrieval time.
- It cannot have a null key but can have multiple null values.
- It maintains ascending order of keys.
- The rest of the properties align with that of HashMap.

**_Hashtable:_**

- It is thread-safe.
- Since it is thread-safe the performance might be low
- Null is not allowed for both key and value