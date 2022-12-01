## Singleton design pattern ##

Singleton design pattern in C# is one of the most popular design patterns. In this pattern, a class has only one instance in the program that provides a global point of access to it. In other words, a singleton is a class that allows only a single instance of itself to be created and usually gives simple access to that instance.
 
There are various ways to implement a singleton pattern in C#. The following are the common characteristics of a singleton pattern.
1. Private and parameterless single constructor
2. Sealed class.
3. Static variable to hold a reference to the single created instance
4. A public and static way of getting the reference to the created instance.

**Advantages of Singleton Design Pattern**
 
- Singleton pattern can implement interfaces.
- Can be lazy-loaded and has Static Initialization.
- It helps to hide dependencies.
- It provides a single point of access to a particular instance, so it is easy to maintain. 

**Disadvantages of Singleton Design Pattern**

Unit testing is a bit difficult as it introduces a global state into an application
Reduces the potential for parallelism within a program by locking.

**Singleton class vs. Static methods**
 
The following compares Singleton class vs. Static methods,
A Static Class cannot be extended whereas a singleton class can be extended.
A Static Class cannot be initialized whereas a singleton class can be.
A Static class is loaded automatically by the CLR when the program containing the class is loaded.
How to Implement Singleton Pattern in C# code
 
- There are several ways to implement a Singleton Pattern in C#.

**Using .NET 4's Lazy<T>** **type**
 
Explanation of the following code:
If you are using .NET 4 or higher then you can use the System.Lazy<T> type to make the laziness really simple.
You can pass a delegate to the constructor that calls the Singleton constructor, which is done most easily with a lambda expression.
Allows you to check whether or not the instance has been created with the IsValueCreated property.
```  
public sealed class Singleton    
{    
    private Singleton()    
    {    
    }    
    private static readonly Lazy<Singleton5> lazy = new Lazy<Singleton5>(() => new Singleton5());    
    public static Singleton5 Instance    
    {    
        get    
        {    
            return lazy.Value;    
        }    
    }    
} 
  ```
