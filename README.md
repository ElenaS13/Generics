# Generics


Generics allow a type or method to operate on objects of various types while providing compile-time safety. The type of objects is checked at compile time so that there are no exceptions at runtime due to incorrect class casting 


ArrayList<E> is a popular Java class that implements a resizable ordered collection using arrays. The method add(E e) appends the element e at the end of the list. The method get(int index) returns the element at the specified position.


The first code snippet compiles correctly, as there is a explicit downcasting in the third line. The object returned by get is converted into an object of Integer. However, the object returned by get is actually of type String and not of type Integer. This bug is not detected at compile time, and the code will throw a ClassCastException at runtime. 

```
ArrayList list1 = new ArrayList();
list1.add("Integer");
Integer value = (Integer) list1.get(0);
```

The second code, however, uses generics, and the incompatibility between types is detected at compile time in the second line, while trying to add an object of type String to an ArrayList that can only store objects of type Integer.

```
ArrayList<Integer> list2 = new ArrayList<Integer>();
list2.add("Integer");
Integer value2 = list2.get(0)
```


When creating an object of a class that uses generics, such as ArrayList<E>, we need to indicate the type that can be stored in this object (e.g., Integer, String, etc.). E is not a valid type in Java. The code below gives a compilation error because E is not a valid type in Java.

```
ArrayList<E> list = new ArrayList<E>();
list.add("a");
list.add(1);
list.add(4.0);
Object value = list.get(0);
```
