# SingleTon_Class_Thread_Safe

/**

 * Write a java program to create a singleton class.
 *
 * @author Firoj
 
 * @since 2022-01-05
 
 */
 

Singleton a class is a class that can have only one instance or object of your class at one time.

Singleton patterns are used ensure that the class will have only one instance and it provides a global access point to that instruction.
 
Let me show you how to implement this Verity of code.

Singleton Steps

a.	Declare the constructor of the class as private.

b.	Declare a static method.

c.	Declare a static member of the same class type in the class.

1. Normal singletone class
   
public class SingletonNormal {

    private static SingletonNormal uniqueInstance;
    private SingletonNormal() {}
    public static SingletonNormal getInstance() {
        if(uniqueInstance == null) {
            uniqueInstance = new SingletonNormal();
        }
        return uniqueInstance;
    }
}

+++++++++++++++++++++++++++++++++++++++++++ Thread Safe Singleton class +++++++++++++++++++++++++++++++++++++++++

2.  singleton class is a class that can only have one instance.
    The SingletonSynchronized class uses the synchronized keyword to ensure that
     only one thread can create an instance of the class at a time.
    
public class SingletonSynchronized {

    private static SingletonSynchronized instance;
    private SingletonSynchronized() {};
    public static synchronized SingletonSynchronized getInstance() {
        if(instance == null) {
            instance = new SingletonSynchronized();
        }
        return instance;
    }
    
}

1. The instance variable is a static variable that is used to store the instance of the SingletonSynchronized class.

2. The constructor of the SingletonSynchronized class is private. This means that the class cannot be instantiated from outside of the class.

3. The getInstance() method is a static method that returns the instance of the SingletonSynchronized class. 
   The getInstance() method is synchronized, which means that only one thread can execute the method at a time.

4. The getInstance() method checks to see if the uniqueInstance variable is null.
   If it is null, then the getInstance() method creates a new instance of the SingletonSynchronized class and stores it in the instance variable.

5. The getInstance() method then returns the instance variable.

  ===================================Double Checking Lock======================================================
  
3. A singleton class is a class that can only have one instance. 
The SingletonDoubleCheckedLocking class uses double-checked locking to ensure that 
only one thread can create an instance of the class at a time.

Double-checked locking is an optimization technique that can improve the performance of singleton classes.
The technique works by checking to see if the instance of the class is null twice, once before entering 
the synchronized block and once after. This can prevent unnecessary synchronization, which can improve the performance of the class.

   public class SingletonDoubleCheckedLocking {
   
    private static SingletonDoubleCheckedLocking instance;
    private SingletonDoubleCheckedLocking() {}
    public static SingletonDoubleCheckedLocking getInstance() {
        if(instance == null) {
            synchronized (SingletonDoubleCheckedLocking.class) {
                if(instance == null) {
                    instance = new SingletonDoubleCheckedLocking();
                }
            }
        }
        return instance;
    }
}


1.The instance variable is a static variable that is used to store the instance of the SingletonDoubleCheckedLocking class.

2. The constructor of the SingletonDoubleCheckedLocking class is private. This means that the class cannot be instantiated from outside of the class.

3. The getInstance() method is a static method that returns the instance of the SingletonDoubleCheckedLocking class.
   The getInstance() method checks to see if the instance variable is null. If it is null, then the getInstance() method enters a synchronized block.

5. Inside the synchronized block, the getInstance() method checks again to see if the instance variable is null.
    If it is still null, then the getInstance() method creates a new instance of the SingletonDoubleCheckedLocking class and stores it in the instance variable.

6. The getInstance() method then returns the instance variable.

&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&& Singleton Eager Instantiation &&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&

4. SingletonEagerInstantiation. A singleton class is a class that can only have one instance.
   The SingletonEagerInstantiation class uses eager instantiation to create an instance of the class when the class is loaded.

Eager instantiation is a simple way to ensure that there is only one instance of a class. 
However, it also means that the instance of the class will be created even if it is not needed. 
This can be a waste of resources, especially if the class is expensive to create.

public class SingletonEagerInstantiation {

    private static SingletonEagerInstantiation uniqueInstance = new SingletonEagerInstantiation();
    private SingletonEagerInstantiation() {}
    public static SingletonEagerInstantiation getInstance() {
        return uniqueInstance;
    }
}

1. The uniqueInstance variable is a static variable that is used to store the instance of the SingletonEagerInstantiation class.

2. The constructor of the SingletonEagerInstantiation class is private
   This means that the class cannot be instantiated from outside of the class.

3. The instance of the SingletonEagerInstantiation class is created when the class is loaded.
   This is because the uniqueInstance variable is initialized with a new instance of the class.

4. The getInstance() method is a static method that returns the instance of the SingletonEagerInstantiation class.
   The getInstance() method simply returns the uniqueInstance variable.




public class TestSingleTonClass {

 public static void main(String[] args) {
 
 If all the instances are same or not. If the instances are same, 
 
 then this is singleton class and singleton instance.
 
 SingletonClass singleton1 = SingletonClass.getInstance();
 
 SingletonClass singleton2 = SingletonClass.getInstance();

Not created because constructor as a private not access the outside class.

// SingletonClass single3=new SingletonClass();

   if (singleton1 == singleton2) {
   
    System.out.println("Both Object are same ");
    
      }
      
      else 
      
      {
      
            System.out.println("Both Object are different");
            
          }
          
      }
      
}


