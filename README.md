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
 This is a singleton class i am going to make as singleton class.
Make this singleton class i need to ensure that there will be a variable which will be a type of singleton class.
There will be a constructor which will be a private constructor.
i don't want this class to be access from outside of this class.
i am create object by using constructor that's reason.
i am going to make class as a private.
class SingletonClass {

I make the as private because should not be access outside this class.
private static SingletonClass instance;
I am going to make constructor as a private show that the object
this class cannot be created outside this class.
private SingletosnClass() {
}

Create a method and that method should return instance of this class(instance).
 public static SingletonClass getInstance() {
 
 This method check instance already exists or not if does not exist.
 then I will return i will create a new instance i will return in the instance.
 already exists then i will return the instance which will already create. Instance is not created.
if (instance == null) {

I need to create instance then send the return it back to this. here i going to check, 
i am going to ensure that in Multithreading environment.
there will be only one thread who will create or can create the instance at a time.
I am going to write synchronized this synchronized.
will have singleton class and this block will check again if the instance
is created or not. if the instance is created then return the instance.
If the instance is not created, then again it is going to create the instance sanded to back.
this approach called as double check login pattern.

// We require lock on the  object or class level. We have a class level lock
synchronized (SingletonClass.class) {

if (instance == null) { //No other thread will access this thread
instance = new SingletonClass();
 }

      }
      
        }
        
      return instance;

      }
      
}

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
      
      else {
            System.out.println("Both Object are different");
          }
      }
}
