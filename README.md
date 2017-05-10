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


##### Generic Method 

We define a class with generics to be able to create instances that handle different types (Integer and String in this case). Therefore the code is correct. The plus sign appends all values calling method toString() to get their String representation, then the last sentence is equivalent to write System.out.println(myClass.get().toString() + yourClass.get().toString()).

```
public class Class<E> {    
    private E attribute;
    
    public void set (E value){
        this.attribute = value;
    }
    
    public E get(){
        return attribute;
    }
}




public static void main(String[] args){
    Class<Integer> myClass = new Class<Integer>();
    Class<String> yourClass = new Class<String>();
    myClass.set(0);
    yourClass.set("0");
    System.out.println(myClass.get() + yourClass.get());
}
```




##### Exercise

In a linked list where we have the references to the first (top) and last (tail) nodes. Which of the following operations is more computationally expensive?

Extracting from the tail.

To extract from the tail we need the reference to the second-to-last node of the list. To get this reference we need to traverse the linked list from the first node.
 



------


To remove the first node in a linked list we need to change the reference stored in top, so that it points to the second element of the list (top = top.getNext();). After running this statement the linked list does not have any reference to the formerly first element of the linked list. The new first element of the list is the formerly second element of the linked list



------
