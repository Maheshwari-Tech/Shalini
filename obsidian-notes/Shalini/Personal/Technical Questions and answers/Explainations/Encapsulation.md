
**WHAT ?**
Encapsulation is **the mechanism of bundling the data (attributes) and methods (functions) that operate on the data into a single unit, known as an object**. It restricts direct access to some of an object's components, which can prevent the accidental modification of data.

Also, it lets the developer put some rules on the _object_ creating and using. But how can we do that? There are 4 keywords for this simple but important action: **_Public_, _Private_, _Default_, _Protected_. We call them _“Access Modifiers”_** and any data structure declaration starts with them.

![[Pasted image 20240617233645.png]]
**PUBLIC** - the “_public_” keyword allows usage wherever, even outside of where it is declared.

**PRIVATE** - It does not allow any usage outside of class that is declared. If we change the _public_ method **run()** to _private_ we cannot use it wherever the _object_ is created.

**PROTECTED** - Inheritance_ allows a **parent-child relationship** between _objects_. With that principle, classes can inherit some methods and variables from other classes and use them. We call “_subclass_” which inherits some data from other classes, and “_superclass_” which is inherited.

**DEFAULT** - The “_default_” access modifier has no keyword. If we don’t write _public_, _private_, or _protected_ that means that the _data structure_ has a _default access modifier_. This access modifier is also restricting some access but not as much as _private_. If a data structure is a _default_, it can be used in the same _package_ but it is not allowed to be used in other packages.

**Difference between “_default_” and “_protected_” steps in here. The _default access modifier_ doesn’t allow for usage outside of its _package_ but _protected_ data structures can be used in _subclasses_ that are outside of its _package_.**


**Through Getter and setter also**.