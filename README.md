# `Java Interview questions`

## What are the main concepts of OOPs in Java?
Object-Oriented Programming or OOPs is a programming style that is associated with concepts like:

1) Inheritance: Inheritance is a process where one class acquires the properties of another.
2) Encapsulation: Encapsulation in Java is a mechanism of wrapping up the data and code together as a single unit.
3) Abstraction: Abstraction is the methodology of hiding the implementation details from the user and only providing the functionality to the users. 
4) Polymorphism: Polymorphism is the ability of a variable, function or object to take multiple forms.

## Why is Java a platform independent language?
Java language was developed in such a way that it does not depend on any hardware or software due to the fact that the compiler compiles the code and then converts it to platform-independent byte code which can be run on multiple systems.

The only condition to run that byte code is for the machine to have a runtime environment (JRE) installed in it.

## Why is Java not a pure object oriented language?
Java supports primitive data types - byte, boolean, char, short, int, float, long, and double and hence it is not a pure object-oriented language.

## Solid principles of java

In Java, SOLID principles are an object-oriented approach that are applied to software structure design. It is conceptualized by Robert C. Martin (also known as Uncle Bob). These five principles have changed the world of object-oriented programming, and also changed the way of writing software. It also ensures that the software is modular, easy to understand, debug, and refactor

- **Single Responsibility Principle(SRP):** Each class should be responsible for a single part or functionality of the system.
- **Open-Closed Principle(OCP):** Software components should be open for extension, but not for modification.
- **Liskov Substitution Principle(LSP):** Objects of a superclass should be replaceable with objects of its subclasses without breaking the system.
- **Interface Segregation Principle(ISP):** No client should be forced to depend on methods that it does not use.
- **Dependency Inversion Principle(DIP):** High-level modules should not depend on low-level modules, both should depend on abstractions.

## Why java does not support multiple inheritance

1) Multiple inheritance is not supported because it leads to deadly diamond problem.
2) In java, every class is a child of Object class. When it inherits from more than one super class, sub class gets the ambiguity to acquire the property of Object class.

For example two class A,B having same method m1(). And class C extends both A, B.

 class C extends A, B // for explaining purpose.

Now, class C will search the definition of m1. First, it will search in class if it didn't find then it will check to parents class. Both A, B having the definition So here ambiguity occur which definition should choose. So java does not support multiple inheritance.

Java supports multiple inheritance through interfaces only. A class can implement any number of interfaces but can extend only one class.

## why top level class could not be static

static keyword is meant for providing memory and executing logic without creating Objects, a class does not have a value logic directly, so the static keyword is not allowed for outer class

If you declare the outer class as static, it will not allow to compile giving : Illegal modifier for the class classname; only public, abstract & final are permitted

## What happens when a main method is declared as private?
When a method is declared as private, the program compiles properly but it will give runtime error. **Main method not public**

## Access specifiers

In Java, methods and data members can be encapsulated by the following four access specifiers. The access specifiers are listed according to their restrictiveness order. 
1) **private:** - accessible within the class where defined
2) **default or package-private:** - when no access specifier is specified
3) **protected:** - accessible only to classes that subclass your class directly within the current or different package
4) **public** - accessible from any class

## static class vs singleton class

Static class always a inner class and static class can create multiple objects. All object have different reference value.

But on the other hand SingleTon class can have only single object because every object reference variable have same reference value.

## What are the characteristics of Java 8? (SHORT)
1) Lambda expressions
2) Functional interfaces
3) Stream API
4) Optional class
5) Date Time API

## What are the characteristics of Java 8? (LONG)

1) Functional Interfaces And Lambda Expressions:

  - In Java 8, a new notion called functional interfaces was introduced. A Functional Interface is an interface that has exactly one abstract method. To designate an interface as a Functional Interface, we don’t need to use the @FunctionalInterface annotation.
	
  - The `@FunctionalInterface` annotation prevents abstract methods from being accidentally added to functional interfaces. It’s similar to a `@Override` annotation, and it’s recommended that you use it. `java.lang.Runnable` is a fantastic example of a functional interface since it has one abstract method, `run ()`.

  - One of the most appealing features of the functional interface is creating objects using lambda expressions. We can create an interface using an anonymous class, but the code is cumbersome. For example:

```
@FunctionalInterface
	public interface FunctionalInterface_one
	{
		public void firstInt_method();
	 
		@Override
		public String toString(); //Overridden from Object class
	 
		@Override
		public boolean equals(Object obj); //Overridden from Object class
	}
```
2) Lambda Expression:

- An anonymous function may be defined as a Lambda Expression (or function) (a function with no name and an identifier). Lambda Expressions are defined precisely where they are required, often as a parameter to another function.
	
- Lambda Expressions implement functional interfaces by implementing the single abstract function provided in the functional interface.

A basic example of the Lambda Expression is:
`(x,y) -> x+y`

The formula above accepts two parameters, x, and y, and returns their total, x+y. The procedure may be used numerous times in different locations depending on the data type of x and y. As a result, the arguments x and y will match int or Integer and string, and depending on the context; it will either add two numbers (if the parameters are int) or concatenate the two strings (when parameters are a string).

```
interface MyInterface
{
     void abstract_func(int x,int y); 
     default void default_Fun()
    {
         System.out.println("This is default method");
    }
}
 class Main
{
     public static void main(String args[])
    {
        //lambda expression
        MyInterface fobj = (int x, int y)->System.out.println(x+y);
 
        System.out.print("The result = ");
        fobj.abstract_func(5,5);
        fobj.default_Fun();
    }
}

```

3) `forEach()` Method In Iterable Interface:

 - In Java 8, the `Java.lang` interface now supports a “forEach” function. 
 - Iterable that can iterate over the collection’s items. The Iterable interface has a default method called “forEach.” 
 - Collection classes use it to iterate items, which extends the Iterable interface.
 - You may send Lambda Expression as an argument to the “forEach” method, which accepts the Functional Interface as a single parameter.

```
importjava.util.ArrayList;
importjava.util.List;
public class Main {
     public static void main(String[] args) {
        List<String> subList = new ArrayList<String>();
        subList.add("Carrot");
        subList.add("Potato");
        subList.add("Cauliflower");
        subList.add("LadyFinger");
        subList.add("Tomato");
        System.out.println("------------Vegetable List--------------");
        subList.forEach(sub -> System.out.println(sub));
  }
}
```

4) Optional Class:

In Java 8, the “java.util” package included an optional class. The public final class “Optional” is used to handle NullPointerException in a Java program. You may give other code or values to execute using Optional. Thus, optional reduces the number of null checks required to avoid a nullPointerException.

You may use the Optional class to prevent the application from crashing and terminating unexpectedly. The Optional class has methods for checking the existence of a value for a given variable.

The following program demonstrates the use of the Optional class.

```
import java.util.Optional; 
public class Main{ 
 
   public static void main(String[] args) { 
        String[] str = new String[10]; 
        Optional<String>checkNull =
                       Optional.ofNullable(str[5]); 
        if (checkNull.isPresent()) { 
            String word = str[5].toLowerCase(); 
            System.out.print(str); 
         } else
           System.out.println("string is null"); 
    } 
}
```
Output:
String is null

To verify whether the string is null in this application, we utilize the Optional class’s “ofNullable” attribute. If it is, the user receives the relevant message.

## Java Stream API For Bulk Data Operations On Collections:

Introduced in Java 8, the Stream API is used to process collections of objects. A stream is a sequence of objects that supports various methods which can be pipelined to produce the desired result.
The features of Java stream are –
- A stream is not a data structure instead it takes input from the Collections, Arrays or I/O channels.
- Streams don’t change the original data structure, they only provide the result as per the pipelined methods.
- Each intermediate operation is lazily executed and returns a stream as a result, hence various intermediate operations can be pipelined. 
- Terminal operations mark the end of the stream and return the result.

Different Operations On Streams-
**Intermediate Operations:**
- map: 
The map method is used to returns a stream consisting of the results of applying the given function to the elements of this stream.
```
List number = Arrays.asList(2,3,4,5);
List square = number.stream().map(x->x*x).collect(Collectors.toList());
```
- filter: 
The filter method is used to select elements as per the Predicate passed as argument.
```
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());
```
- sorted: 
The sorted method is used to sort the stream.
```
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().sorted().collect(Collectors.toList());
```
**Terminal Operations:**
- collect: 
The collect method is used to return the result of the intermediate operations performed on the stream.
```
List number = Arrays.asList(2,3,4,5,3);
Set square = number.stream().map(x->x*x).collect(Collectors.toSet());
```
- forEach: 
The forEach method is used to iterate through every element of the stream.
```
List number = Arrays.asList(2,3,4,5);
number.stream().map(x->x*x).forEach(y->System.out.println(y));
```
- reduce: 
The reduce method is used to reduce the elements of a stream to a single value. The reduce method takes a BinaryOperator as a parameter.
```
List number = Arrays.asList(2,3,4,5);
int even = number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i);
```
## Java Date Time API
Java 8 introduced new APIs for Date and Time to address the shortcomings of the older java.util.Date and java.util.Calendar.

Local: Simplified date-time API with no timezone management complexity.
Zoned: specialized date-time API that can handle several time zones.

- Issues With the Existing Date/Time APIs
1) **Thread safety** – The Date and Calendar classes are not thread safe, leaving developers to deal with the headache of hard-to-debug concurrency issues and to write additional code to handle thread safety. On the contrary, the new Date and Time APIs introduced in Java 8 are immutable and thread safe, thus taking that concurrency headache away from developers.
2) **API design and ease of understanding** – The Date and Calendar APIs are poorly designed with inadequate methods to perform day-to-day operations. The new Date/Time API is ISO-centric and follows consistent domain models for date, time, duration and periods. There are a wide variety of utility methods that support the most common operations.
3) **ZonedDate and Time** – Developers had to write additional logic to handle time-zone logic with the old APIs, whereas with the new APIs, handling of time zone can be done with Local and ZonedDate/Time APIs.

#### Working With LocalDate

The LocalDate represents a **date in ISO format (yyyy-MM-dd) without time**. An instance of current date can be created from the system clock:
```
LocalDate localDate = LocalDate.now();
```
And we can get the LocalDate representing a specific day, month and year by using the of method or the parse method.
For example, these code snippets represent the LocalDate for February 20, 2015:
```
LocalDate.of(2015, 02, 20);
LocalDate.parse("2015-02-20");
```
The following code snippet gets the current local date and adds one day:
```
LocalDate tomorrow = LocalDate.now().plusDays(1);
```
#### Working With LocalTime

The LocalTime represents **time without a date**.
```
LocalTime now = LocalTime.now();
```

#### Working With LocalDateTime

LocalDateTime is used to represent a **combination of date and time**. This is the most commonly used class when we need a combination of date and time.
```
LocalDateTime.now();
```

#### Using ZonedDateTime API

Java 8 provides ZonedDateTime when we need to deal with **time-zone-specific date and time**. The ZoneId is an identifier used to represent different zones. There are about 40 different time zones, and the ZoneId represents them as follows.

Here, we create a Zone for Paris:
```
ZoneId zoneId = ZoneId.of("Europe/Paris");
```
And we can get a set of all zone ids:
```
Set<String> allZoneIds = ZoneId.getAvailableZoneIds();
```
The LocalDateTime can be converted to a specific zone:
```
ZonedDateTime zonedDateTime = ZonedDateTime.of(localDateTime, zoneId);
```
The ZonedDateTime provides the parse method to get time-zone-specific date-time:
```
ZonedDateTime.parse("2015-05-03T10:15:30+01:00[Europe/Paris]");
```

## String:

In Java, a String is represented internally by an array of byte values. strings are immutable to improve performance and security.

**Benefits to having immutable strings:**

1) The string pool is only possible if the strings, once created, are never changed, as they are supposed to be reused
2) The code can safely pass a string to another method, knowing that it can't be altered by that method
3) Immutably automatically makes this class thread-safe
4) Since this class is thread-safe, there is no need to synchronize common data, which in turn improves performance
5) Since they are guaranteed to not change, their hashcode can be easily cached

**How Is a String Stored in Memory?**

According to the JVM Specification, String literals are stored in a runtime constant pool, which is allocated from the JVM's method area.

**how many strings are allocated:**

- The JVM stores only one copy of a particular String in the pool
- When creating a new String, the JVM searches in the pool for a String having the same value
- If found, the JVM returns the reference to that String without allocating any additional memory
- If not found, then the JVM adds it to the pool (interns it) and returns its reference

## What is the difference between equals() and == in Java?

Equals() method is defined in Object class in Java and used for checking equality of two objects defined by business logic.

“==” or equality operator in Java is a binary operator provided by Java programming language and used to compare primitives and objects. public boolean equals(Object o) is the method provided by the Object class. The default implementation uses == operator to compare two objects. For example: method can be overridden like String class. equals() method is used to compare the values of two objects.

## Difference between Abstract Class and Interface in Java

As we know that abstraction refers to hiding the internal implementation of the feature and only showing the functionality to the users. i.e. what it works (showing), how it works (hiding). Both abstract class and interface are used for abstraction, henceforth Interface and Abstract Class are required prerequisites

**1) Type of methods:** 
Interface can have only abstract methods. An abstract class can have abstract and non-abstract methods. From Java 8, it can have default and static methods also.
**2) Final Variables:**
Variables declared in a Java interface are by default final. An abstract class may contain non-final variables.
**3) Type of variables:** 
Abstract class can have final, non-final, static and non-static variables. The interface has only static and final variables.
**4) Implementation:**
Abstract class can provide the implementation of the interface. Interface can’t provide the implementation of an abstract class.

**access specifiers that can be used by interfaces and abstract classes:**
- **Interface:** Public or default
- **Abstract Class:** (Anything ) : public , private or Default

## Inheritance vs Abstraction: 
1) A Java interface can be implemented using the keyword “implements” and an abstract class can be extended using the keyword “extends”.
2) Multiple implementations: 
An interface can extend another Java interface only, an abstract class can extend another Java class and implement multiple Java interfaces.
3) Accessibility of Data Members: 
Members of a Java interface are public by default. A Java abstract class can have class members like private, protected, etc.

## What is the difference between Array list and vector in Java?

ArrayList and Vectors both implement the List interface, and both use (dynamically resizable) arrays for their internal data structure, much like using an ordinary array. 

**ArrayList:** ``` ArrayList<T> al = new ArrayList<T>(); ```
**Vector:** ``` Vector<T> v = new Vector<T>(); ```

| Array list | vector |
| ------ | ------ |
| ArrayList is not synchronized. | Vector is synchronized. |
| ArrayList increments 50% of the current array size if the number of elements exceeds ts capacity. | Vector increments 100% means doubles the array size if the total number of elements exceeds its capacity. |
| ArrayList is not a legacy class. It is introduced in JDK 1.2. | Vector is a legacy class. |
| ArrayList is fast because it is non-synchronized. | Vector is slow because it is synchronized, i.e., in a multithreading environment, it holds the other threads in a runnable or non-runnable state until the current thread releases the lock of the object. |
| ArrayList uses the Iterator interface to traverse the elements. | A Vector can use the Iterator interface or Enumeration interface to traverse the elements. |


## What makes a HashSet different from a TreeSet?

| Key | Hash Set | Tree Set |
| ------ | ------ | ------ |
| Implementation  | Hash set is implemented using HashTable  | The tree set is implemented using a tree structure.  |
| Null Object  | HashSet allows a null object  | The tree set does not allow the null object. It throws the null pointer exception.  |
| Methods  | Hash set use equals method to compare two objects  | Tree set use compare method for comparing two objects. |
| Heterogeneous object  | Hash set doesn't now allow a heterogeneous object  | Tree set allows a heterogeneous object  |
| Ordering  | HashSet does not maintain any order  |  TreeSet maintains an object in sorted order  |


## Difference between ArrayList and LinkedList

ArrayList and LinkedList both implements List interface and maintains insertion order. Both are non synchronized classes.

| ArrayList | LinkedList |
| ------ | ------ |
| ArrayList internally uses a dynamic array to store the elements. | LinkedList internally uses a doubly linked list to store the elements. |
| Manipulation with ArrayList is slow because it internally uses an array. If any element is removed from the array, all the bits are shifted in memory. | Manipulation with LinkedList is faster than ArrayList because it uses a doubly linked list, so no bit shifting is required in memory. |
| An ArrayList class can act as a list only because it implements List only. | LinkedList class can act as a list and queue both because it implements List and Deque interfaces. |
|ArrayList is better for storing and accessing data. | LinkedList is better for manipulating data. |

```
import java.util.*;
class TestArrayLinked {
    public static void main(String args[]) {

        List < String > al = new ArrayList < String > (); //creating arraylist    
        al.add("Ravi"); //adding object in arraylist    
        al.add("Vijay");
        al.add("Ravi");
        al.add("Ajay");

        List < String > al2 = new LinkedList < String > (); //creating linkedlist    
        al2.add("James"); //adding object in linkedlist    
        al2.add("Serena");
        al2.add("Swati");
        al2.add("Junaid");

        System.out.println("arraylist: " + al);
        System.out.println("linkedlist: " + al2);
    }
}
```
## What are the differences between HashMap and HashTable in Java?

| Hashmap | Hashtable |
| ------ | ------ |
| No method is synchronized. | Every method is synchronized. |
| Multiple threads can operate simultaneously and hence hashmap’s object is not thread-safe. | At a time only one thread is allowed to operate the Hashtable’s object. Hence it is thread-safe. |
| Threads are not required to wait and hence relatively performance is high. | It increases the waiting time of the thread and hence performance is low. |
| Null is allowed for both key and value. | Null is not allowed for both key and value. Otherwise, we will get a null pointer exception. |

```
public static void main(String args[])
    {
        //----------hashtable -------------------------
        Hashtable<Integer,String> ht=new Hashtable<Integer,String>();
        ht.put(101," ajay");
        ht.put(101,"Vijay");
        ht.put(102,"Ravi");
        ht.put(103,"Rahul");
        System.out.println("-------------Hash table--------------");
        for (Map.Entry m:ht.entrySet()) {
            System.out.println(m.getKey()+" "+m.getValue());
        }
 
        //----------------hashmap--------------------------------
        HashMap<Integer,String> hm=new HashMap<Integer,String>();
        hm.put(100,"Amit");
        hm.put(104,"Amit"); 
        hm.put(101,"Vijay");
        hm.put(102,"Rahul");
        System.out.println("-----------Hash map-----------");
        for (Map.Entry m:hm.entrySet()) {
            System.out.println(m.getKey()+" "+m.getValue());
        }
    }
```

## What is the importance of reflection in Java?

Reflection is a runtime API for inspecting and changing the behavior of methods, classes, and interfaces. 
Java Reflection allows you to analyze classes, interfaces, fields, and methods during runtime without knowing what they are called at compile time. 
Reflection can also be used to create new objects, call methods, and get/set field values. 
External, user-defined classes can be used by creating instances of extensibility objects with their fully-qualified names. 
Debuggers can also use reflection to examine private members of classes.

Reflection can be used to get information about –

1) **Class:** The ```getClass()``` method is used to get the name of the class to which an object belongs.
2) **Constructors:** The ```getConstructors()``` method is used to get the public constructors of the class to which an object belongs.
3) **Methods:** The ```getMethods()``` method is used to get the public methods of the class to which an objects belongs.

```
// A simple Java program to demonstrate the use of reflection
import java.lang.reflect.Method;
import java.lang.reflect.Field;
import java.lang.reflect.Constructor;
  
// class whose object is to be created
class Test
{
    // creating a private field
    private String s;
  
    // creating a public constructor
    public Test()  {  s = "GeeksforGeeks"; }
  
    // Creating a public method with no arguments
    public void method1()  {
        System.out.println("The string is " + s);
    }
  
    // Creating a public method with int as argument
    public void method2(int n)  {
        System.out.println("The number is " + n);
    }
  
    // creating a private method
    private void method3() {
        System.out.println("Private method invoked");
    }
}
  
class Demo
{
    public static void main(String args[]) throws Exception
    {
        // Creating object whose property is to be checked
        Test obj = new Test();
  
        // Creating class object from the object using
        // getclass method
        Class cls = obj.getClass();
        System.out.println("The name of class is " +
                            cls.getName());
  
        // Getting the constructor of the class through the
        // object of the class
        Constructor constructor = cls.getConstructor();
        System.out.println("The name of constructor is " +
                            constructor.getName());
  
        System.out.println("The public methods of class are : ");
  
        // Getting methods of the class through the object
        // of the class by using getMethods
        Method[] methods = cls.getMethods();
  
        // Printing method names
        for (Method method:methods)
            System.out.println(method.getName());
  
        // creates object of desired method by providing the
        // method name and parameter class as arguments to
        // the getDeclaredMethod
        Method methodcall1 = cls.getDeclaredMethod("method2",
                                                 int.class);
  
        // invokes the method at runtime
        methodcall1.invoke(obj, 19);
  
        // creates object of the desired field by providing
        // the name of field as argument to the 
        // getDeclaredField method
        Field field = cls.getDeclaredField("s");
  
        // allows the object to access the field irrespective
        // of the access specifier used with the field
        field.setAccessible(true);
  
        // takes object and the new value to be assigned
        // to the field as arguments
        field.set(obj, "JAVA");
  
        // Creates object of desired method by providing the
        // method name as argument to the getDeclaredMethod
        Method methodcall2 = cls.getDeclaredMethod("method1");
  
        // invokes the method at runtime
        methodcall2.invoke(obj);
  
        // Creates object of the desired method by providing
        // the name of method as argument to the 
        // getDeclaredMethod method
        Method methodcall3 = cls.getDeclaredMethod("method3");
  
        // allows the object to access the method irrespective 
        // of the access specifier used with the method
        methodcall3.setAccessible(true);
  
        // invokes the method at runtime
        methodcall3.invoke(obj);
    }
}
```

Output:
```
The name of class is Test
The name of constructor is Test
The public methods of class are : 
method2
method1
wait
wait
wait
equals
toString
hashCode
getClass
notify
notifyAll
The number is 19
The string is JAVA
Private method invoked
```

## Difference between HashMap and ConcurrentHashMap

HashMap is the Class which is under Traditional Collection and ConcurrentHashMap is a Class which is under Concurrent Collections.

HashMap is non-Synchronized in nature i.e. HashMap is not Thread-safe whereas ConcurrentHashMap is Thread-safe in nature.
HashMap performance is relatively high because it is non-synchronized in nature and any number of threads can perform simultaneously. But ConcurrentHashMap performance is low sometimes because sometimes Threads are required to wait on ConcurrentHashMap.
While one thread is Iterating the HashMap object, if other thread try to add/modify the contents of Object then we will get Run-time exception saying ConcurrentModificationException.Whereas In ConcurrentHashMap we won’t get any exception while performing any modification at the time of Iteration.

## Object Serialization:

Serialization is a mechanism of converting the state of an object into a byte stream. The byte array can be the class, version, and internal state of the object.

Deserialization is the reverse process where the byte stream is used to recreate the actual Java object in memory. This mechanism is used to persist the object.

**Case 1: If the superclass is serializable, then subclass is automatically serializable**
If the superclass is Serializable, then by default, every subclass is serializable. Hence, even though subclass doesn’t implement Serializable interface( and if its superclass implements Serializable), then we can serialize subclass object.

**Case 2: If a superclass is not serializable, then subclass can still be serialized**
Even though the superclass doesn’t implement a Serializable interface, we can serialize subclass objects if the subclass itself implements a Serializable interface. So we can say that to serialize subclass objects, superclass need not be serializable. But what happens with the instances of superclass during serialization in this case. The following procedure explains this.

**Case 2(a): What happens when a class is serializable, but its superclass is not?**
Serialization: At the time of serialization, if any instance variable inherits from the non-serializable superclass, then JVM ignores the original value of that instance variable and saves the default value to the file.

## How to stop serilalize
By using **transient** keyword

```
// A sample class that uses transient keyword to
// skip their serialization.
class Test implements Serializable
{
    // Making password transient for security
    private transient String password;
  
    // Making age transient as age is auto-
    // computable from DOB and current date.
    transient int age;
  
    // serialize other fields
    private String username, email;
    Date dob;
  
    // other code
}
```

## What is a classloader in Java?

The Java ClassLoader is a subset of JVM (Java Virtual Machine) that is responsible for loading the class files. Whenever a Java program is executed it is first loaded by the classloader. Java provides three built-in classloaders:

Bootstrap ClassLoader
Extension ClassLoader
System/Application ClassLoader

## User-defined Custom Exception in Java

An exception is an issue (run time error) that occurred during the execution of a program. When an exception occurred the program gets terminated abruptly and, the code past the line that generated the exception never gets executed.

Java provides us the facility to create our own exceptions which are basically derived classes of Exception. 
Creating our own Exception is known as a custom exception or user-defined exception. 
Basically, Java custom exceptions are used to customize the exception according to user needs. 
In simple words, we can say that a User-Defined Exception or custom exception is creating your own exception class and throwing that exception using the ‘throw’ keyword.

Why use custom exceptions?
Java exceptions cover almost all the general types of exceptions that may occur in the programming. However, we sometimes need to create custom exceptions.

Following are a few of the reasons to use custom exceptions:

To catch and provide specific treatment to a subset of existing Java exceptions.
Business logic exceptions: These are the exceptions related to business logic and workflow. It is useful for the application users or the developers to understand the exact problem.

## Design patterns:

A design pattern provides a general reusable solution for the common problems that occur in software design. 
The pattern typically shows relationships and interactions between classes or objects. 
The idea is to speed up the development process by providing well-tested, proven development/design paradigms. 
Design patterns are programming language independent strategies for solving a common problem. 
That means a design pattern represents an idea, not a particular implementation. 
By using design patterns, you can make your code more flexible, reusable, and maintainable.

##### Types of Design Patterns
1) Creational 
These design patterns are all about class instantiation or object creation.
Creational design patterns are the Factory Method, Abstract Factory, Builder, Singleton, Object Pool, and Prototype. 

2) Structural
These design patterns are about organizing different classes and objects to form larger structures and provide new functionality. 
Structural design patterns are Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Private Class Data, and Proxy. 

## Singleton Design Pattern

The singleton pattern is one of the simplest design patterns. 
Sometimes we need to have only one instance of our class for example a single DB connection shared by multiple objects as creating a separate DB connection for every object may be costly. Similarly, there can be a single configuration manager or error manager in an application that handles all problems instead of creating multiple managers

The singleton pattern is a design pattern that restricts the instantiation of a class to one object. 
```
// Classical Java implementation of singleton
// design pattern
class Singleton
{
    private static Singleton obj;
 
    // private constructor to force use of
    // getInstance() to create Singleton object
    private Singleton() {}
 
    public static Singleton getInstance()
    {
        if (obj==null)
            obj = new Singleton();
        return obj;
    }
}
```
Here we have declared getInstance() static so that we can call it without instantiating the class. The first time getInstance() is called it creates a new singleton object and after that, it just returns the same object. Note that Singleton obj is not created until we need it and call getInstance() method. This is called lazy instantiation.

## Runnable vs Callable

| Runnable | Callable |
| ------ | ------ |
| It is a part of java.lang package | It is a part of the java.util.concurrent package |
| It cannot return the return of computation. | It can return the result of the parallel processing of a task. |
| It cannot throw a checked Exception. | It can throw a checked Exception. |
| In a runnable interface, one needs to override the run() method in Java. | In order to use Callable, you need to override the call() |
| Runnable.run() returns void | Callable.call() returns a generic value V  |

**Runnable Example:**
```
public interface Runnable {
    public void run();
}

public class EventLoggingTask implements  Runnable{
    private Logger logger
      = LoggerFactory.getLogger(EventLoggingTask.class);

    @Override
    public void run() {
        logger.info("Message");
    }
}
```
**Callable Example:**
```
public interface Callable<V> {
    V call() throws Exception;
}

public class FactorialTask implements Callable<Integer> {
    int number;

    // standard constructors

    public Integer call() throws InvalidParamaterException {
        int fact = 1;
        // ...
        for(int count = number; count > 1; count--) {
            fact = fact * count;
        }

        return fact;
    }
}
```

## How to create Immutable class in Java?

Immutable class in java means that once an object is created, we cannot change its content. In Java, all the wrapper classes (like Integer, Boolean, Byte, Short) and String class is immutable. We can create our own immutable class as well. 

- The class must be declared as final so that child classes can’t be created.
- Data members in the class must be declared private so that direct access is not allowed.
- Data members in the class must be declared as final so that we can’t change the value of it after object creation.
- A parameterized constructor should initialize all the fields performing a deep copy so that data members can’t be modified with an object reference.
- Deep Copy of objects should be performed in the getter methods to return a copy rather than returning the actual object reference)

```
// Java Program to Create An Immutable Class

// Importing required classes
import java.util.HashMap;
import java.util.Map;

// Class 1
// An immutable class
final class Student {

	// Member attributes of final class
	private final String name;
	private final int regNo;
	private final Map<String, String> metadata;

	// Constructor of immutable class
	// Parameterized constructor
	public Student(String name, int regNo,
				Map<String, String> metadata)
	{

		// This keyword refers to current instance itself
		this.name = name;
		this.regNo = regNo;

		// Creating Map object with reference to HashMap
		// Declaring object of string type
		Map<String, String> tempMap = new HashMap<>();

		// Iterating using for-each loop
		for (Map.Entry<String, String> entry :
			metadata.entrySet()) {
			tempMap.put(entry.getKey(), entry.getValue());
		}

		this.metadata = tempMap;
	}

	// Method 1
	public String getName() { return name; }

	// Method 2
	public int getRegNo() { return regNo; }

	// Note that there should not be any setters

	// Method 3
	// User -defined type
	// To get meta data
	public Map<String, String> getMetadata()
	{

		// Creating Map with HashMap reference
		Map<String, String> tempMap = new HashMap<>();

		for (Map.Entry<String, String> entry :
			this.metadata.entrySet()) {
			tempMap.put(entry.getKey(), entry.getValue());
		}
		return tempMap;
	}
}

// Class 2
// Main class
class GFG {

	// Main driver method
	public static void main(String[] args)
	{

		// Creating Map object with reference to HashMap
		Map<String, String> map = new HashMap<>();

		// Adding elements to Map object
		// using put() method
		map.put("1", "first");
		map.put("2", "second");

		Student s = new Student("ABC", 101, map);

		// Calling the above methods 1,2,3 of class1
		// inside main() method in class2 and
		// executing the print statement over them
		System.out.println(s.getName());
		System.out.println(s.getRegNo());
		System.out.println(s.getMetadata());

		// Uncommenting below line causes error
		// s.regNo = 102;

		map.put("3", "third");
		// Remains unchanged due to deep copy in constructor
		System.out.println(s.getMetadata());
		s.getMetadata().put("4", "fourth");
		// Remains unchanged due to deep copy in getter
		System.out.println(s.getMetadata());
	}
}
```
output:
```
ABC
101
{1=first, 2=second}
{1=first, 2=second}
{1=first, 2=second}
```

## Fail Fast And Fail Safe Iterators in Java

Iterators in java are used to iterate over the Collection objects.

**Fail-Fast**
- Fail-Fast iterators immediately throw ConcurrentModificationException if there is a structural modification of the collection. 
- Structural modification means adding, removing any element from collection while a thread is iterating over that collection. 
- Iterator on ArrayList, HashMap classes are some examples of fail-fast Iterator.

**Fail-Safe**
- Fail-Safe iterators don’t throw any exceptions if a collection is structurally modified while iterating over it. 
- This is because, they operate on the clone of the collection, not on the original collection and that’s why they are called fail-safe iterators. 
- Iterator on CopyOnWriteArrayList, ConcurrentHashMap classes are examples of fail-safe Iterator.


## Garbage collection

- Garbage collection in Java is the process by which Java programs perform automatic memory management. 
- Java programs compile to bytecode that can be run on a Java Virtual Machine. 
- When Java programs run on the JVM, objects are created on the heap, which is a portion of memory dedicated to the program. 
- Eventually, some objects will no longer be needed. The garbage collector finds these unused objects and deletes them to free up memory.
- The main objective of Garbage Collector is to free heap memory by destroying unreachable objects. 
- The garbage collector is the best example of the Daemon thread as it is always running in the background. 

Important Concepts Related to Garbage Collection in Java
- **Unreachable objects:** 

  An object is said to be unreachable if it doesn’t contain any reference to it. Also, note that objects which are part of the island of isolation are also unreachable. 
  
```
  Integer i = new Integer(4);
// the new Integer object is reachable  via the reference in 'i' 
i = null;
// the Integer object is no longer reachable.
```
- **Using Runtime.getRuntime().gc() method:**
  Runtime class allows the application to interface with the JVM in which the application is running. Hence by using its gc() method, we can request JVM to run Garbage Collector.

 - **Finalization:** 
Just before destroying an object, Garbage Collector calls finalize() method on the object to perform cleanup activities. Once finalize() method completes, Garbage Collector destroys that object.
finalize() method is present in Object class with the following prototype.
protected void finalize() throws Throwable


# `Spring and Spring Boot Interview Questions`

## What is Spring Framework?

Spring is a powerful open-source, loosely coupled, lightweight, java framework meant for reducing the complexity of developing enterprise-level applications. This framework is also called the “framework of frameworks” as spring provides support to various other important frameworks like JSF, Hibernate, Structs, EJB, etc.

## What are the features of Spring Framework?
- Spring framework follows a layered architecture pattern that helps in the necessary components selection along with providing a robust and cohesive framework for J2EE applications development.
- The AOP (Aspect Oriented Programming) part of Spring supports unified development by ensuring separation of the application’s business logic from other system services.
- Spring provides highly configurable MVC web application framework which has the ability to switch to other frameworks easily.
- Provides provision of creation and management of the configurations and defining the lifecycle of application objects.
- Spring has a special design principle which is known as IoC (Inversion of Control) that supports objects to give their dependencies rather than looking for creating dependent objects.
- Spring is a lightweight, java based, loosely coupled framework.
- Spring provides a generic abstraction layer for transaction management that is also very useful for container-less environments.
- Spring provides a convenient API to translate technology-specific exceptions (thrown by JDBC, Hibernate or other frameworks) into consistent, unchecked exceptions. This introduces abstraction and greatly simplifies exception handling.

## What do you mean by IoC (Inversion of Control) Container?

Spring container forms the core of the Spring Framework. The Spring container uses Dependency Injection (DI) for managing the application components by creating objects, wiring them together along with configuring and managing their overall life cycles. The instructions for the spring container to do the tasks can be provided either by XML configuration, Java annotations, or Java code.

## What do you understand by Dependency Injection?

The main idea in Dependency Injection is that you don’t have to create your objects but you just have to describe how they should be created.

The components and services need not be connected by us in the code directly. We have to describe which services are needed by which components in the configuration file. The IoC container present in Spring will wire them up together.

In Java, the 2 major ways of achieving dependency injection are:
- Constructor injection: Here, the IoC container invokes the class constructor with a number of arguments where each argument represents a dependency on the other class.
- Setter injection: Here, the spring container calls the setter methods on the beans after invoking a no-argument static factory method or defa

## What are Spring Beans?

- They are the objects forming the backbone of the user’s application and are managed by the Spring IoC container.
- Spring beans are instantiated, configured, wired, and managed by IoC container.
- Beans are created with the configuration metadata that the users supply to the container (by means of XML or java annotations configurations.)

## What are the bean scopes available in Spring?
The Spring Framework has five scope supports. They are:

- **Singleton:** The scope of bean definition while using this would be a single instance per IoC container.
- **Prototype:** Here, the scope for a single bean definition can be any number of object instances.
- **Request:** The scope of the bean definition is an HTTP request.
- **Session:** Here, the scope of the bean definition is HTTP-session.
- **Global-session:** The scope of the bean definition here is a Global HTTP session.
Note: The last three scopes are available only if the users use web-aware ApplicationContext containers.

## Explain Bean life cycle in Spring Bean Factory Container.

- The IoC container instantiates the bean from the bean’s definition in the XML file.
- Spring then populates all of the properties using the dependency injection as specified in the bean definition.
- The bean factory container calls `setBeanName()` which take the bean ID and the corresponding bean has to implement BeanNameAware interface.
- The factory then calls `setBeanFactory()` by passing an instance of itself (if BeanFactoryAware interface is implemented in the bean).
- If BeanPostProcessors is associated with a bean, then the `preProcessBeforeInitialization()` methods are invoked.
- If an init-method is specified, then it will be called.
- Lastly, postProcessAfterInitialization() methods will be called if there are any BeanPostProcessors associated with the bean that needs to be run post creation.


## Explain the advantages of using Spring Boot for application development.
- Spring Boot helps to create stand-alone applications which can be started using java.jar (Doesn’t require configuring WAR files).
- Spring Boot also offers pinpointed ‘started’ POMs to Maven configuration.
- Has provision to embed Undertow, Tomcat, Jetty, or other web servers directly.
- Auto-Configuration: Provides a way to automatically configure an application based on the dependencies present on the classpath.
- Spring Boot was developed with the intention of lessening the lines of code.
- It offers production-ready support like monitoring and apps developed using spring boot are easier to launch

## What are the features of Spring Boot?
- **Spring Boot CLI** – This allows you to Groovy / Maven for writing Spring boot application and avoids boilerplate code.
- **Starter Dependency** – With the help of this feature, Spring Boot aggregates common dependencies together and eventually improves productivity and reduces the burden on
- **Spring Initializer** – This is a web application that helps a developer in creating an internal project structure. The developer does not have to manually set up the structure of the project while making use of this feature.
- **Auto-Configuration** – This helps in loading the default configurations according to the project you are working on. In this way, unnecessary WAR files can be avoided.
- **Spring Actuator** – Spring boot uses actuator to provide “Management EndPoints” which helps the developer in going through the Application Internals, Metrics etc.
- **Logging and Security** – This ensures that all the applications made using Spring Boot are properly secured without any hassle.

## Spring ApplicationContext

Spring ApplicationContext is where Spring holds instances of objects that it has identified to be managed and distributed automatically. These are called beans.

Bean management and the opportunity for dependency injection are some of Spring's main features.

Using the Inversion of Control principle, Spring collects bean instances from our application and uses them at the appropriate time. We can show bean dependencies to Spring without needing to handle the setup and instantiation of those objects.

The ability to use annotations like @Autowired to inject Spring-managed beans into our application is a driving force for creating powerful and scalable code in Spring


## Annotations in spring boot

Spring Annotations are a form of metadata that provides data about a program. Annotations are used to provide supplemental information about a program. It does not have a direct effect on the operation of the code they annotate. It does not change the action of the compiled program.

1) **@SpringBootApplication**
	@SpringBootApplication annotation is one point replacement for using @Configuration, @EnableAutoConfiguration and @ComponentScan annotations alongside their default attributes.
	
2) **@Autowired**
	@Autowired annotation is applied to the fields, setter methods, and constructors. It injects object dependency implicitly. We use @Autowired to mark the dependency that will be injected by the Spring container.	
	
3) **@Qualifier**
	If more than one bean of the same type is available in the container, the framework will throw NoUniqueBeanDefinitionException, indicating that more than one bean is available for autowiring
	
	Ex. incase we have interface with multiple implementation then this issue will rails to avoid this issue we are using the @qulifier annotation.

4) **@Component**
@Component is an annotation that allows Spring to automatically detect our custom beans.

In other words, without having to write any explicit code, Spring will:

- Scan our application for classes annotated with @Component
- Instantiate them and inject any specified dependencies into them
- Inject them wherever needed

Stereotype Annotations
Spring Framework provides us with some special annotations. These annotations are used to create Spring beans automatically in the application context. @Component annotation is the main Stereotype Annotation. There are some Stereotype meta-annotations which is derived from @Component those are

1 **@Service:** We specify a class with @Service to indicate that they’re holding the business logic. Besides being used in the service layer, there isn’t any other special use for this annotation. The utility classes can be marked as Service classes.

2 **@Repository:** We specify a class with @Repository to indicate that they’re dealing with CRUD operations, usually, it’s used with DAO (Data Access Object) or Repository implementations that deal with database tables.

3: **@Controller:** We specify a class with @Controller to indicate that they’re front controllers and responsible to handle user requests and return the appropriate response. It is mostly used with REST Web Services.

