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

//No other thread will access this thread

if (instance == null) {

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
      
      else 
      
      {
      
            System.out.println("Both Object are different");
            
          }
          
      }
      
}









Singleton a class is a class that can have only one instance or object of your class at one time.

 Singleton patterns are used ensure that the class will have only one instance and it provides a global access point to that instruction.
 
Let me show you how to implement this Verity of code.

Singleton Steps

a.	Declare the constructor of the class as private.

b.	Declare a static method.

c.	Declare a static member of the same class type in the class.

class Singleton{

//Declare a static member of the same class type in the class.

private static Singleton instance;

//Declare the constructor pf the class as private.

private Singleton(){

}

//Declare a static method.

public static Singleton getInstance(){

if(instance==null){

instance=new Singleton();// We don’t want to return this instance every time this getInstance is called 

}// We don’t want to return create a new instance will do that only check this if(instance==null).

return instance;

       }
       
}

public class Test{

public static void main(String args[]){

Singleton s1=Singleton.getInstance();

Singleton s2=Singleton.getInstance();

Sop(s1==s2);

   }
   
}// Output is : True

For Example: If have two thread which are trying to create an instance of Singleton class.

public static Singleton getInstance(){

//The first thread enter this if(instance==null) it will do this check and about to create an instance.

instance=new Singleton(); in the meantime another thread come and does this check.

if(instance==null) even before the first thread create in this instance instance=new Singleton();  thread. 

This expression here if(instance==null) evaluate to true. 

It will go on and meantime the first thread would out create instance instance=new Singleton();

and second thread also create an instance having two instance Void this problem.

public static Singleton getInstance(){

        if(instance==null){

       instance=new Singleton();

   }
       return instance;
       
    }

}

Java Mark this method as Synchronized.

public static synchronized Singleton getInstance(){

if(instance==null){

instance=new Singleton();

}

return instance;

    }
    
}



class Singleton{

//Declare a static member of the same class type in the class.

// To mark static variable as volatile. Do avoid any issues in a multithreaded environment.

private static volatile Singleton instance;

//Declare the constructor pf the class as private.

private Singleton(){

}
Make sure that this method will be access only by one thread at a time.

Make our code even better remove the keyword here mark this block if(instance==null) as synchronized.

public static synchronized Singleton getInstance(){

// Use synchronized with in the Bereket 

//And require the lock within the object or class. We have a class level lock

if(instance==null){

synchronized(Singleton.class){ //the block is start here

if(instance==null){ After this if block

instance=new Singleton();

   }
         }//Will end here
}

return instance;

    }
    
}


Eger Initialization

public class Singleton{

//Declare a static member of the same class type in the class.

private static Singleton instance=new Singleton();

//Declare the constructor of the class as private.

private Singleton(){
}
//Declare a static method.

public static Singleton getInstance(){

return instance;

    }
}

Second Approach

public class Singleton{

//Declare a static member of the same class type in the class.

private static Singleton instance;

//Static blocks execute class is loaded in memory.

static{

instance=new Singleton();

}

//Declare the constructor pf the class as private.

private Singleton(){

}
//Declare a static method.

public static Singleton getInstance(){

return instance;

    }
    
}
