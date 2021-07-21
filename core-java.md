## Mock Interview

### 

### 1. Core Java

#### 1.1 Basic

- Environment
  - JDK, JRE, JVM
  - naming rule
  - command line: compile, execution
- JVM
  - Permanent Generation
    - static 
  - Stack
    - main function
    - primitive types
    - reference
      - comparison, ==, equals()
      - pass by value
      - final
      - volatile
  - Heap
    - object creation
    - string pool 
    - GC
- OOP
  - Polymorphism
    - Overload
    - Override
  - Inheritance
    - Extension, implementation
    - diamond issue
    - casting
  - Encapsulation(wrap the variable and method together as a unit)
    - Accessibility: public, protected, package level, private
  - Abstraction
    - Abstract class
    - interface



------



1. what's JDK, JRE, JVM?

   - JDK: java development kit
     - it consists of JRE and Development Tools(like: java interpreter, compiler: javac, archiver: jar, documentation generator: javadoc, etc.)
   - JRE: java runtime environment
     - provides minimum requirements for executing a java application.
     - it consists of JVM, core classes and other library classes.
   - JVM: has three aspects of definition
     - A specification where specify the working of java virtual machine.
     - An implementation: is a computer program that meets the requirements of jvm specification
     - Runtime Instance: once we run the java class, an instance of jvm is created, it' s like class and object.
     - .class file is executable under jvm

   ![](https://media.geeksforgeeks.org/wp-content/uploads/JDK_JRE_JVM_x.jpg)

2. What's environment variable, PATH, CLASSPATH, JAVA_HOME?

   - environment variable
     - global system variable accessible by all the processes running under the Operating system.(example: USERNAME, OS, SystemRoot, PATH)
   - PATH
     - maintains a list of directories, **The OS searches the PATH entries for executable programs**, like: java compiler(javac) and Java Runtime(java)
   - CLASSPATH:
     - maintains a list of directories(containing many java class files)  and jar file. 
     - The java compiler and java runtime searches the CLASSPATH entries for java classes referenced in program
   - JAVA_HOME
     - maintain the locations of JDK and JRE installed directly, respectively.

3. What's naming rule of java file and class

   - one java file can only have at most one public outer class
   - this public outer class should has the same name as the file name

4. whether a file is executable?

   - a file is executable, this depends on the environment
     - .java file is executable under the javac, but not under jvm
     - .class file is executable under jvm

5. how to compile and execute the java file in command line

   - javac HW.java
     - create a HW.class file
   - java HW
     - execute the class file
   - java -jar HW.jar
     - execute the jar file

6. How many kinds of class loader?

   - three kinds
     - Bootstrap class loader
     - Extension class loader
     - application class loader

   ![](https://www.javainterviewpoint.com/java-virtual-machine-architecture-in-java/jvm-architecture/)

7. why replace the permGen with MetaSpace?

   - in java 8
   - **reduces the chance to get the OutOfMemoryError**

8. how does jvm work?

   - jvm is a java process
   - whenever the jvm starts, it'll start a main thread and launch the main method
   - Every thread has it's own stack
   - machine codes are put into the stack and executed line by line.

9. how to create an object(new an object)

   - look for the class from permanent generation
   - allocate a piece of memory for the object in the heap
   - create the object by jvm(specify the inner address in object)
   - call the constructor (constructor is the last step when we create an object)

10. what's reference in java

- reference in java stores the type, name and the address of the object it refers to
- which is stored in the stack, help us to find the object

11. what jvm is composed of ?

    - permanant generation, which stores class level information
    - stack, stores thread level information
      - each thread has a stack
    - heap, stores object level information

12. how many primitive types in java

    - there are **eight** types of primitives.
    - they are directly stored in the stack.
    - each of them has corresponding wrapper types.
      - byte(8 bit)
      - short, char (2 byte)
      - int, float (4 byte)
      - long, double (8 byte)
      - boolean

13. what's the type of address in the reference?

    - it's int, which is 4 bytes(32 bits)
    - since the address is 32 bit, the total address bit of memory is 32 bit
    - so the jvm is 32 bit

14. static vs non-static

    - static is class level, whenever added become class level, stored in perm gen
    - non-static is object-level, stored in heap
    - we cannot access non-static field/method in static method, because they are stored in different area(one is perm gen, anther is stack)

15. what's main function

    - main function is the entry point of any java program.
    - Its syntax is always `public static void main(String[] args){}`
    - main function should be static, since it should be available when we execute the function which means it should be class level function
    - `String[] args` is called as java command line arguments, 
      - `java HW 1 2 3`
    - when jvm starts and load all the class into the permGen, it'll look for `main() ` function and start main thread
    - copy the instructions in the main() function into the stack.
    - execute the instructions in the stack

16. how to create object of public static inner class

    - public static inner class can be seen a an outer class
    - OuterClass.InnerClass ic1 =  new OuterClass.InnerClass1();

17. how to create an object of non-static public inner class

    - since it's non-static, it's not class level, 
    - `OuterClass oc = new OuterClass();`
    - `OuterClass.InnerClass2 ic2 = oc.new InnerClass2();`

18. What's characteristics of Non-static nested classes

    - are so called inner classes, 
    - a nested class is a member of its enclosing class.
    - Non-static inner class have access to other members of the enclosing class
    - static inner class do not have access to other members of the enclosing class

19. Four OOP fundamental concepts

    - Polymorphism(override and overload)
      - a concept that we can perform a single action in different ways
    - Inheritance( extension , is a relation)
      - a mechanism in which one class acquires all the properties and behaviors of a parent class
    - Encapsulation( has a relation)
      - a mechanism of wrapping the data and method together as a single unit.
    - Abstraction
      - a process of hiding the implementation details and showing only functionality to the user

20. how does java achieve abstraction

    - by abstract class and interface

21. what's **abstract** in java

    - abstract is a java keyword
    - which can be added before method and class
    - to represent this class function is unimplemented

22. what are function components

    - modifier(public, static, final)
    - return type
    - function name
    - arguments/parameters
    - function body(abstract no body)

23. what's abstract class in java

    - any class with abstract keyword can become an abstract class
    - class with abstract method has to be an abstract class, abstract method can only exist in abstract class and interface
    - abstract class can have concrete method
    - abstract class cannot be instantiated
    - when extends abstract class, we have to implement all the abstract methods, or declare it as abstract class
    - abstract class can extends concrete class( Object class is a concrete class)

24. what's interface in java

    - <java 7 , all the methods in the interface should be public abstract(can be ignored)
    - ,>java 8, static/default method can be not abstract, with method body
    - public static final field allowed in the interface

25. what's extension in java

    - class can only extends one class but can implements multiple interfaces
    - in java, all classes (except: Object) can have one parent
    - interface can extends one/**more **interface???(because methods don't have implementation? >java 8, extends from two interfaces with same default methods, will be forced to provide implementation for the default method)
    - subclass have to implement abstract methods in super class

26. Diamond issue

    when one class extends two classes with same method extended from the same parent classes, cause ambiguity don't know which method to call

27. what's upcasting in java

    Assign an object to its parent class reference, which is always allowed in java

28. what' downcasting in java

    downcasting is not always allowed in java, only when this situation is allowed

    ```java
    Parent p = new Child();
    Child c = (Child) p;
    ```



28. what's overload in java
    - within the same class
    - same method name, different arguments(different number | different type)
    - return type can be same/different,not necessary
    - `public void methodName(args)`
    - main() method can be overloaded, even though it's static method
    - it's compile time polymorphism
29. what's override in java
    - Override only happens in object level 

- Override is a feature that allows a **subclass** to **provide a specific implementation** of a method that is **already provided** by one of its super-classes or parent classes。
  - same signature: method name + arguments
  - modifier
    - **private **method cannot be overridden(cannot be seen from outside)
    - package/protected/public become more accessible
  - return type 
    - should be "is a " relationship
    - more general
  - **static/final/private** function cannot be overridden
    - static function stored in the perm gen, 
    - final method's reference cannot be changed
    - private method cannot be accessed by sub classes
    - package level method can only be overridden within same package
  - superclass throws exception, subclass cannot 

30. what's **constructor** in java

    - it's an object level method, no return type specified, same name as the class
    - if it's not specified, jvm will provide a constructor by default
    - constructor will be invoked by keyword new, **used to initialize the object**
    - this(),super() should be in the first line

31. Accessibility in java

    - work as **information hidding**
    - four modifier: public, protected, package level, private
    - public
      - can be access anywhere
    - protected
      - can be accessed within the same package or sub classes
      - different package, sub class (extends parent class), protected(static/non-static) method extends from parent class can be accessed (non-static method can access both, static method can access static protected method)
    - package level
      - can be accessed within the same package
    - private
      - can only be accessed within the same class

32. Is java passing by reference or passing by value

    - pass by reference
      - means that memory address of the variable is passed to the method
    - pass by value
      - means that the value stored in the memory is passed to the method
    - **java is always passing by value**, 
      - even though it's an object reference
      - pass by reference means the variable's address, even though the object reference is object's address, it's not the variable's pointer
      - it's not the address on stack, it's address on heap(main memory)
    - an primitive type
      - value is stored in the reference
    - an object reference
      - the address is stored in the reference, pass the address to the method

33. what's the difference between final, finally, finalize

    - Briefly, final is a keyword,
    - finally is used in try-catch-finally block, which is use to execute some code like closing connection, stream, etc.
    - **finalize** is kind of **a method** that **garbage collector** always **calls before the destroying the object**

    ```java
    //The object which is eligible for Garbage Collection, that object’s corresponding class finalize method is going to be executed
    
    class Hello { 
    	public static void main(String[] args) 
    	{ 
    		String s = new String("RR"); 
    		s = null; 
    
    		// Requesting JVM to call Garbage Collector method 
    		System.gc(); 
    		System.out.println("Main Completes"); 
    	} 
    
    	// Here overriding finalize method 
    	public void finalize() 
    	{ 
    		System.out.println("finalize method overriden"); 
    	} 
    } 
    
    // ------------------------------
    //We can call finalize method Explicitly then it will be executed just like normal method call but object won’t be deleted/destroyed
    
    ```



34. what's final in java

    - Basically, final is a keyword in java
    - which can be added to class/method/field
    - **final class cannot be extended**
    - **final method cannot be overridden**
    - **final field cannot be changed when it's primitive and reassigned when it's object reference**

35. how to assign a value to a final field

    - when it's static final field(**constructor is object level**)

      - assign the value when declaration

      - assign the value in static block

        ```java
        static final Y
        static {
            y10;
        }
        ```

    - when it's non-static

      - assign the value while declaration

      - assign the value in the code block

        ```java
        final in m;
        {
            n=10;
        }
        ```

      - assign the value in the constructor

36. how to implement immutable class in java

    - Basically, an immutable class is a class that all objects created from this class cannot be modified during the runtime
    - characteristics
      - private all the fields
      - no setters, only getters
      - define constructors for initialize
      - should not provide any function for modifying the object
      - **final the class** to make it unable to be extended, prevent from overriding method
      - to avoid any field from being modified,
        1. make the field immutable(**Collections.unmodifiableList**/Set/Map)
        2. return a copy of its field, like ThreadLocal
    - Java has no immutable class by using reflection
    - String is a kind of immutable class
    - 

37. what's naming rule of getter

    - return type should be the same as field type
    - function name = getFieldName/isFieldName, if it's boolean
    - return the field back
    - no parameter

38. String is an immutable class in java

    - once the String content changed, it'll refer to another different object

    ```java
    String s1 = "abc";
    String s2 = s1;
    System.out.println(s1==s2);//true, compare the reference address value
    s1 +="d";
    System.out.println(s1==s2);//false
    
    ```

39. difference between final vs immutable

    - final avoid changing the reference
    - immutable avoid changing the object fields

40. What's reflection in java

    Basically we create object from class, **Reflection is get the class from the object**.

    - reflection is based on the **getClass()** method,
    - wanna change the field: **setAccessible(true)**
    - we can use reflection to change any object even though is field is private

    ```java
    Immutable im1 = new Immutable(1,"Yu","Shi",new ArrayList<String>());
    Immutable im2 = im1;
    Field fieldId = im1.getClass().getDeclaredField("id");
    System.out.println(im1.getId());
    fieldId.setAccessible(true);
    fieldId.set(im1, 2);
    System.out.println(im1.getId());
    System.out.println(im1==im2);
    
    // results:
    // 1
    // 2
    // true
    ```

41. Comparison in java

    - ==, compare the reference
      - compare the type
      - compare the value (primitive value,   address)
    - equals(), specify the rule we compare two objects
      - to Compare String, we normally compare hashCode() of the String

42. what's string pool in java

    String pool is string constant pool, which is stored in the java heap memory

    - String pool use **flyweight design pattern**

    - once we use double quotes,

    - it'll automatically look for the String with the same value in the string pool.

      - if so, it'll return found String address

      - if not, it'll create a new String object in the string pool and return the value.

      - if using **new** to create a String object, it'll create a String in the heap anyway.

      - ```java
        String s = new String("xyz");
        // two String objects are created in the heap, one is in the heap, another is in string pool
        ```

43. what's Meta Space in java

    - it's a java 8 feature
    - it's out of the jvm, in the memory, permanent generation now in the meta space
    - because, permenant generation is not able to load that much class file, when the project become so large

44. how does garbage collection work in java

    - Basically, garbage collector is a **daemon thread** in the stack, **help us to collect garbage**

    - definition of garbage is that, if **an object doesn't have reference**, it can be considered as garbage

    - Workflow

      - the heap is divided into two part: one is **young generation**, another is **tenured generation**
      - new objects are created in the **Eden space**
      - garbage collector will do **minor GC** in young generation
      - if the object generated **in eden space  has reference** it'll be moved to **Survivor I** and then **Survivor II**, back and forth.
      - After several times,  find the object have been detected **used for several times**, it'll be moved to **Tenured Generation**
      - when old generation is gonna be swept. **all the other threads will be suspended **whenever garbage collector is doing **major GC**

      ![](C:\Users\Yu Shi\Pictures\resourcesOL\markdown\mock_interview\GC_Heap.png)

45. how to invoke garbage collector?

    - System.gc();
    - Runtime.getRuntime().gc()
    - not directly garbage collecting, will schedule to garbage collecting

------

#### 1.2 Exception Handling

46. What's Exception handling in java

    - Exception is an **error event that can happen during the runtime** of a program and **disrupts the normal flow**
    - Java provides a **robust and object oriented way to handle exception scenarios**, which is known as Java Exception handling

47. Java Exception Hierarchy

    ![](https://www.manishsanger.com/wp-content/uploads/2018/03/Exception-Hierarchy.png)

48. what's Throwable in java

    - **Throwable is a concrete class**, other ables are interface
    - Throwable is the superclass of Error and Exception

49. what's Error and Exception in java

    - Error is a subclass of Throwable that **indicates serious problems** that a reasonable application **should not try to catch**
    - Exception are events that **occur during the execution** of programs that **disrupt the normal flow of instructions**.

50. What's checked and unchecked exceptions in java

    - checked exceptions are **checked during compile time**
    - unchecked exceptions are **checked during runtime**
    - **Error and RuntimeException are unchecked, other Exceptions are checked exception**

  

51. List some Errors, checked exceptions and unchecked exceptions

- error(are unchecked)
  - StackOverflowError
  - OutOfMemoryError
- checked Exception
  - FileNotFoundException
  - ClassNotFoundException
  - SQLException
  - IOExeption
- unchecked Exception(runtimeException)
  - NullPointerException
  - IndexOutOfBoundException

49. is Error a Throwable

    - yes, error extends Throwable, it is a Throwable

50. how to handle checked exception

    1. Declare the exception using **throws** keyword
    2. handle the exception using try-catch blocks

51. how to catch multiple exceptions

    - using multiple catch block to catch multiple exception

    - using | pipe symbol to declare multiple Exceptions like

      ```java
      try{
          
      }catch(NullPointerException|IOException e){
          e.printStackTrace();
      }
      ```

52. what does finally block do

    - finally block will be executed no matter what happens
    - unless JVM shutdown before finally block
    - normally use finally block to **close resources**
    - can be replaced by **try with resources** after java 7

53. can constructor throws Exception

    - yes, **constructor can throws Exception**

54. what's try with resources

    - resources automatically close **when try block is finished** before block
    - resources can be any object created from the class which implements **AutoClosable**( which has only one method, close() method)



------

#### 1.3 IO

- java bean
- Cloneable, clone()
- Serialize
  - Serializable
    - requirements : implements Serializable + fields implements Serializable
    - customize
      - transient
      - static, `serialVersionUID`
      - Externalizable
- Deserialize
  - Serializable : Reflection
  - Externalizable : Constructor + setters
- IO
  - Design pattern : decorator
  - binary file class
    - InputStream : FileInputStream, BufferedInputStream, DataInputStream, ObjectInputStream
  - character file class
- NIO



------



1. what's java bean

   - a *serializable* POJO (plain old Java object), 
     - with a no-argument constructor
     - private fields 
     - with getters/setters

2. what's POJO

   plain old java object,

3. what's Object.toString()

   - used for displaying the object information

   - when we print the object out, it'll automatically call the toString() method

     ```java	
     User u = new User();
     System.out.println(u);
     
     ```

4. what's clone() method in Object Class

   - super.clone() method (native method in the Object class)is a shallow copy, only copy the reference, not copy the entire object
   - the object which call the clone() method should implements Cloneable.

   ```java
   protected native Object clone() throws CloneNotSupportedException
   
   ```

5. What's Cloneable in java

   - Cloneable is a marker interface in java, which without any methods
   - which work like an annotation tell the jvm that **this object got the right to be cloned**

6. marker interface

   - Example : **Cloneable**, **Serializable**
   - marker interface : empty interface without fields and methods, **used to indicate some information to compiler or JVM**
   - Cloneable :  tell jvm the object has the right to be cloned
   - Serializable : get the right to convert the state of an object into a byte stream.

7. why we need shallow copy

   - if the object is too large
   - we can modify the field we need, and keep others the same
   - if we need to change the field, we need reassign

8. can you write a Cloneable Java Bean?

   ```java
   public class Computer implements Cloneable{
       
       @Override
       public Computer clone(){
           Computer c = null;
           try{
   			c = (Computer)super.clone();       		}catch(CloneNotSupportedException e){
           e.printStackTrace();    
           }
           return c;
       }
   }
   
   ```

9. how to use FileInputStream / FileOutputStream to read and write

   ```java
   // write
   try(FileOutputStream fos = new FileOutputStream("resources/test1.dat");){
       int[] nums = {1,2,3,4,5};
       for(int x:nums) {
           fos.write(x);
       }
       System.out.println("Complete");
   }catch(){
       
   }
   
   // read
   try(FileInputStream fis = new FileInputStream("resources/test1.dat");){
       int x = fis.read();
       while(x!=-1) {
           System.out.println("%d",x);
           x = fis.read();
       }
   }catch(Exception e){
       
   }
   
   ```

10. how to read/write entire data from/into the file

    ```java
    // write int, double, boolean
    int i = -5;
    double d = 3.14;
    boolean b = true;
    try(FileOutputStream fos = new FileOutputStream("resources/test2.dat");
    BufferedOutputStream bos = new DataOutputStream(fos);
    DataOutputStream dos = new DataOutputStream(bos);){
        dos.writeInt(i);
        dos.writeDouble(d);
        dos.writeBoolean(b);
        System.out.println("Done");
    }catch(Exception e){
        
    }
    
    // read
    try(FileInputStream fis = new FileInputStream("resources/test2.dat");
    BufferedInputStream bis = new BufferedInputStream(fis);
    DataInputStream dis = new DataInputStream(bis);){
        // order matters
        int i = dis.readInt();
        double d = dis.readDouble();
        boolean b = dis.readBoolean();
    }catch(Exception e){
        
    }
    
    ```

11. how to read/write object (**Serializable**) in java

    - First of all, the object should created from class which implements **Serializable**

    ```java
    // write
    Tank t = new Tank("50mm",50000);
    try(FileOutputStream fos = new FileOutputStream("resources/test3.dat");
    ObjectOutputStream oos = new ObjectOutputStream(fos);){
        oos.writeObject(t);
        System.out.println("Done");
    }
    
    // read
    try(FileInputStream fis = new FileInputStream("resources/test3.dat");
    ObjectInputStream ois = new ObjectInputStream(fis);){
        Tank t = (Tank) ois.readObject();
        System.out.println(t);
    }catch(Exception e){
        
    }
    
    ```

12. how to read/write Externalizable in java

    - same as Serializable

13. what's binary file class hierarchy

    - input/output
    - InputStream is abstract class implements Autoclosable

    ![](https://www.researchgate.net/profile/Muhammad_Sohaib_Ayub/publication/322696527/figure/fig3/AS:644646753562634@1530707171551/5Java-I-O-Class-Hierarchy-Input-stream-and-output-stream-are-classes-and-both-consist-of.png)

    - `FileInputStream` only work with **one byte**
    - `BufferedInputSteam` **store the bytes** read by the FileInputStream
    - `DataInputStream` helps us to **cut the stream**(int, double, boolean specific)
    - `ObjectInputStream` can **read Object** and deserialize it from stream
    - usage
      - primitive types
        - `FileInputStream` + `BufferedInputStream` + `DataInputStream`
      - objects
        - `FileInputStream` + `ObjectInputStream`

14. what's the design pattern used in input and output Stream

    - Decorator, creates a decorator class which wraps the original class and provides additional
      functionality

    ```java
    interface Pizza{}
    class PlainPizza implements Pizza{}
    class ToppingDecorator implements Pizza{
        Pizza pizzaTemplate;
        // override
    }
    class Pepperoni extends ToppingDecorator{}
    
    ```

    

15. what's Adapter design pattern

    - convert one object into another object
    - when we call the API, BUT the parameters are different from the object we have, so we use adapter to convert the object

16. what's Serializable in java

    - Serializable is an marker interface in java,
    - when we use ObjectInputStream to read/write an object into file, the object to be read/written should implements **Serializable**
    - or will cause **NotSerializableException**

17. what's **transient** in java

    - transient is a keyword

    - which only used in front of field

      only effect serialization

    - **transient field won't written into the file**

18. End Of File = -1

19. does deserialize need an constructor?

    - No, deserialization doesn't need constructor to create the object
    - deserialization use **reflection** to create the object

20. whether static field can be serialized

    - static field is class level
    - Static variables belong to a class and not to any individual instance. The concept of serialization is concerned with the object's current state. 
    - only data associated with a specific instance of  a class is serialized
    - therefore static member fields are ignored during seriealization
    - **only one static field can be serialized: **
      - private static final long **serialVersionUID** = 1234222L;

21. what's serialVersionUID?

    - when we transfer the data among several systems. use the same Object, should with the same UID

22. how to serialize static field in java

    - using Externalizable 
    - with which we can customize the serialize/deserialize
    - the **order of writeExternal()/readExternal() should be the same**
    - **need default constructor** to create an object to readExternal()

23. whether serialization need constructor?

    - using Serializable DOES NOT require constructor
    - using **Externalizable** DOES **require default constructor**

24. How does Serializable / Externalizable **deserialized**?

    - Serializable : use reflection to deserialize
    - Externalizable : use constructor to create object and use setters to set the fields

25. what's NIO

    - non-blocking IO, 
    - which using channel (double direction)
    - **Blocking IO**, using streams(single direction), thread wait for the src to write/read

26. can we read/write transient or static field?

    - implements Externalizable, provide readExternal()/writeExternal()

27. if we are using Serializable, can we customize serialization?

    - yes, we can 
    - we can provide `private void writeObject()`/`private void readObjct()` methods
    - they will be automatically called by the jvm

28. if we want to serialize an object,

    - not only this class should implements Serializable
    - but also **the fields of the class should be Serializable**

29. how to write an **Externalizable**

    ```java
    public class Aircraft implements Externalizable{
        private int size;
    	private String model;
    	private String make;
    	
        // have to provide a default constructor to create an object to readExternal()
        public Aircraft(){
            super();
        }
        @Override
        public void writeExternal(ObjectOutput out) throws IOException{
            out.writeInt(size);
            out.writeObject(model);
            out.writeObject(make);
        }
        @Override
        public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException{
            this.size = in.readInt();
            this.model = (String) in.readObject();
            this.make = (String) in.readObject();
        }
    }
    
    ```



------

#### 1.4 Multithreading and Concurrency

- definition, pros & cons
- Thread creation
  - extends Thread
  - implements Runnable
  - implements Callable 
    - With return type - call() 
    - Future<v> work as placeholder to return value
  - Thread Pool 
    - submit the Runnable/Callable
    - framework - Executors
- Thread life cycle
  - Runnable - t.start()
  - waiting - wait() / notify() / Thread.sleep()
- avoid race condition
  - synchronized
  - dead lock
    - java.util.concurrent package
    - Lock , ReentrantLock
- Thread safe 
  - data structure - BlockingQueue
- Object thread related methods
  - wait()
  - notify() / notifyAll()
  - join(), wait for referenced thread to terminate
  - yield(), give up current usage of processor
- Daemon thread



------



1. what's multithreading

   - multithreading is **a process executing multiple threads simultaneously**.

2. what's the benefits of multithreading

   - it'll **raise the performance**

3. what's the problem of multithreading

   - it'll cause **race condition** to shared resource
   - **deadlock**

4. how to create a thread object

   1. from a class which **extends Thread class**, in this case, cannot extends other superclass,
   2. **implements Runnable Interface**, in this case can extends other superclass

   - both of them should **override the run() method**

5. how many ways to create a new thread

   1. ```java
      public static class MyThread extends Thread{
          @Override
          public void run(){
              System.out.println("Thread");
          }
      }
      
      ```

   2. ```java
      public static class MyRunnable implements Runnable{
          @Override
          public void run(){
              System.out.println(
      "Runnable");
          }
      }
      
      ```

      

      ```java
      public static void main(){
          MyThread mt = new MyThread();
          MyRunnable mr = new MyRunnable();
          Thread t = new Thread(mr);
          
          t.run();//directly run the run, not execute in a new thread
          
          
          mt.start();
          t.start();
          // start a thread
      }
      
      ```

6. what's process of **start()** method

   - execute the start() method of thread object(t.start();)
   - ask jvm to **create a new thread**
   - give the thread to **task/thread scheduler**
   - the task scheduler will **find time to execute the run()** method of the thread object in a new thread

7. how to **run a thread**

   - if extends Thread Class, just call the start() method of the thread object
   - if implements Runnable interface, pass the Runnable into the Thread constructor and call the start() method

8. what's **thread life cycle**

   - init ( create Thread obj)
   - Runnable (give the thread to jvm thread scheduler,after start() )
   - Running (execute the run() method of thread object )
   - waiting (once the thread is sleep, block on I/O, wait for lock, suspend(), wait())
   - waiting ( sleep done, I/O complete, lock available, resume(), notify(), notifyAll())
   - End/complete/terminated (run() method exits or stop() )

   ![](https://simplesnippets.tech/wp-content/uploads/2018/06/thread-lifecycle-diagram-in-java.jpg)

9. what's synchronized

   - synchronized means **happens in order**
   - synchronized is a java **keyword**, which can be added in front of a **method / code block**
   - in java, **every class/object has a lock**
   - synchronized method need **access authority** to be accessed
   - a class can have synchronized methods and non-synchronized methods, only synchronized methods accessing need authority, others don't need, can directly access

10. when does main thread end, and when does jvm end

    - **main thread** ended **after executing all the program in the main method**, no matter how many threads are running
    - **jvm will terminate** when there's **only daemon thread running**

11. what's thread hang up?

    some threads stuck in waiting status forever, jvm will never terminated

12. What's the process of **inter-thread communication**

    ![](https://static.javatpoint.com/images/core/interthread.gif)

    - divided into three parts
      - entry list : all the thread first time come to **acquire the lock**
      - waiting area : after thread acquire the lock and **wait() or notify()**
      - on deck : executing
    - thread enter to acquire the lock
    - certain

    ```java
    synchronized(d) {
        d.wait();	// the object with lock call the wait() method
        
        d.notify();
    }
    
    ```

    

13. **Atomic Variables**

    - Atomic variables allow us to perform atomic operations on the variables
    - atomic operations are operations that **ALWAYS execute together**
    - `i++`, on simple operation can be divided into several assembly operation
      - read
      - add
      - write
    - atomic classes 
      - AtomicInt
      - AtomicLong
      - AtomicBoolean
      - AtomicReference : used for any type of object

14. **Volatile keyword**

    - volatile variable directly read from/write to main memory(heap), solve the variable visibility problem
    - avoid code reordering
    - http://tutorials.jenkov.com/java-concurrency/volatile.html

15. **volatile vs atomic**

16. what's **wait()** method of an object

    - wait() method is from Object class
    - which put current thread from **on deck** into **waiting area**(from running status to waiting status)
    - **wait()** method should be in the **synchronized block** (should already got the lock , and is in the on deck area)
    - **synchronized block**

    ```java
    synchronized(t1) {
    	System.out.println(id + " got " + t1);	try {
    		Thread.sleep(1000);
    	} catch(InterruptedException e) {
    		e.printStackTrace();
    	}
    }
    
    ```

    - **synchronized method**

    ```java
    	synchronized public static void foo() {
    		System.out.println(Thread.currentThread().getName()+", foo");
    		try {
    			Thread.sleep(2000);
    		} catch (InterruptedException e) {
    			e.printStackTrace();
            }
    	}
    
    ```

    

17. what's notify() method in java

    - it's Object class method
    - public final void notify()
    - final method, cannot be overridden
    - randomly notify one thread in the waiting area into the entry list( **change the state of thread from waiting to runnable**)

18. what's  notifyAll() 

    - notify all the threads in the waiting area

19. where wait()/notify() is called

    - `synchronized(d){}`
    - synchronized who, call who's wait()/notify() methods

20. what's deadlock in java

    - a deadlock is a state in which **each member of a group is waiting for anther**, including itself, to take action like releasing a lock normally
    - Deadlock happens between two threads
    - a state that both threads hold the lock of certain object and waiting the other

21. what's  the solution to **deadlock**

    java.util.concurrent package

22. what's lock in java

    - **Lock is an interface** in java.util.concurrent package
    - it's an object level solution similar to synchronized
    - it contains **lock(), unlock(), tryLock()** methods

23. what's **ReentrantLock** in java

    - ReentrantLock is a concrete class implements Lock interface
    - and **provide synchronization to methods while accessing shared resources**
    - it **replace the lock of object as well as synchronized**
    - the code that manipulate the shared resources is surrounded by calls to lock and unlock method like sychronized, which gives a lock to current thread and block others
    - as the name says, reentrantlock allow thread  to enter inter lock on a resource more than once, there's a hold count which will increase and decrease when we lock and unlock 
    - ReentrantLock also provide a fairness parameter, by which the lock would abide by the order of the lock request

24. how to use ReentrantLock

    - surround the code with calls to lock() and unlock() method
    - call tryLock() to get a boolean, which marks whether the lock is free to enter, it can work together with if-else clause

    ```java
    // call lock(), unlock	
    public void some_method() 
    { 
    		reentrantlock.lock(); 
    		try
    		{ 
    			//Do some work 
    		} 
    		catch(Exception e) 
    		{ 
    			e.printStackTrace(); 
    		} 
    		finally
    		{ 
    			reentrantlock.unlock(); 
    		} 
    		
    } 
    
    // call tryLock(), unlock()
    
    	boolean res1 = l1.tryLock();
    	if(res1) {
    		try {								
            	System.out.println(id + " got " + l1);												Thread.sleep(1000);
    		} catch (InterruptedException e) {
    			e.printStackTrace();
            }
    
            boolean res2 = l2.tryLock();
    
            if(res2) {
                System.out.println(id + " got "+ l2);
                l2.unlock();
            } else {
                System.out.println(id + " cannot get" + l2 + "leaving...");
            }
    
            l1.unlock();
        } else {
            System.out.println(id + " cannot get" + l1 + "leaving...");
        }
    
    ```

25. ExecutorService

    - A framework provided by JDK which **simplifies the execution of tasks in asynchronous mode**
    - **provides a pool of threads and API for assigning tasks to it**
    - ExecutorService is an interface
    - from java.util.concurrent package

    **Structure**

    ![](https://miro.medium.com/max/866/1*Jn7umQaToVoOJfXaR3IHkg.jpeg)

    **Hierarchy**

    ![](https://examples.javacodegeeks.com/wp-content/uploads/2019/10/Thread_Executor_Hierarchy_W.jpg)

    

26. what's Callable in java

    - Callable is an interface which is like Runnable, but has return type with the call() method whereas run() method return void
    - if don't give generic, it'll return Object

27. what's thread pool in java

    - a thread pool is a collection of pre-initialized threads
    - it's kind of shared thread resources

28. what's Future<V> in java

    - Future is an interface,
    - which has cancel(), isCancelled(), isDone(), get(), get(long,TimeUnit) these methods
    - String pool will allocate an address when we deploy the task Callable(which has a return type)
    - The future is bonded with the thread

29. how many kind of thread pool

    - unlimited thread
      - `ExecutorService es = Executors.newCachedThreadPool();`
    - limited thread
      - `ExecutorService es = Executors.newFixedThreadPool(5);`
    - single thread
      - `ExecutorService es =  Executors.newSingleThreadExecutor();`

30. how to use ThreadPool in java

    ```java
    public static class SmartThread implements Callable{
        int id;
        
        @Override
        public Integer call() throws Exception{
            return id;
        }
    }
    
    public static void testThreadPool() {
    
        ExecutorService es = Executors.newCachedThreadPool();
    
        List<Future<Integer>> futures = new ArrayList<>();
    
        for(int i=0;i<10;i++){
            Future<Integer> f = es.submit(new SmartThread(i));
            futures.add(f);
        }
        for(int i=0;i<futures.size();i++) {
            Future<Integer> f = future.get(i);
            while(!f.isDone()){
                //wait
            }
            try{
                System.out.println(f.get());
            }catch(Exception e){
                e.printStackTrace();
            }
        }
        es.shutDown();
    }
    
    ```

31. what's BlockingQueue in java

    - it's an **interface**, which is typically used to have one thread produces and another consumes， **follows producer and consumer**
    - it's implementation concrete classes are threadsafe
      - LinkedBlockingQueue
    - a producing thread will be blocked if the blockingqueue reach the capacity
    - a consuming thread will also blocked if the blockingQueue is empty

32. how does blockingQueue work

    - BlockingQueue<Integer> bq = new LinkedBlockingQueue<Integer>(5);
    - bq.put(i);
    - int x = bq.take();

    ```java
    	public static class Producer implements Runnable {
    		
    		BlockingQueue<Integer> bq;
    
    		public Producer(BlockingQueue<Integer> bq) {
    			this.bq = bq;
    		}
    		@Override
    		public void run() {
    			for(int i=0;i<100;i++) {
    
    				try {
    					bq.put(i);
    					System.out.println("Producing ->" + i);
    					Thread.sleep(500);	
    				}catch(Exception e) {
    					e.printStackTrace();
    				}
    				
    			}
    		}
    	}
    	
    	public static class Consumer implements Runnable {
    		
    		BlockingQueue<Integer> bq;
    
    		public Consumer(BlockingQueue<Integer> bq) {
    			this.bq = bq;
    		}
    		@Override
    		public void run() {
    			try {
    				Thread.sleep(3000);
    				while(!bq.isEmpty()) {
    					int x = bq.take();
    					System.out.println("Consuming ---->" + x);
    					Thread.sleep(500);
    
    				}
    			}catch(Exception e) {
    				e.printStackTrace();
    			}
    		}
    	}
    	public static void main(String[] args) {
    		BlockingQueue<Integer> bq = new LinkedBlockingQueue<Integer>(5);
    		Producer p = new Producer(bq);
    		Consumer c = new Consumer(bq);
    		new Thread(p).start();
    		new Thread(c).start();
    	}
    
    
    ```

33. what's thread safe in java

    - it describe that the object in the heap whether it's thread safe

34. what's the difference between threadsafe and deadlock

    - deadlock 
      - describe the states of two threads stuck forever
    - threadsafe describe one object under multithreading situation

35. ways to ensure the threadsafe

    1. synchronized/lock
    2. immutable
    3. return a  copy, threadLocal

36. what's join() of Thread in java

    - join() method
    - current thread object wait for the referenced thread object to terminate, it'll be turned into waiting state
    - used when we need to get the result before some where

    ```java
    	public static void main(String[] args) {
    		int x = 3, y = 5;
    		Add a = new Add(x,y);
    		Multiply m = new Multiply(x,y);
    		
    		a.start();
    		m.start();
    		
    		try {
    			//main thread join the threads created by the a/m thread object
    			a.join();
    			m.join();
    		}catch(Exception e) {
    			e.printStackTrace();
    		}
    
    		System.out.println(m.getRes() - a.getRes());
    		System.out.println("Complete!");
    	}
    
    ```

37. what's yield() in java

    - Thread.yield()
    - a hint to scheduler that this thread is willing to give up current use of the processor,

38. can a thread start() twice

    - No, it cannot, it'll generate IllegalThreadStateException
    - one thread object can be only start() once
    - even after join() method
    - it has a flag to mark whether the thread object has been start()
    - so we can use reflection to modify the field to start() it again

39. what's daemon thread

    - if jvm has only daemon thread running, the jvm will shut down, which doesn't prevent the jvm from existing.
    - daemon thread is running in the background
    - garbage collection is a daemon thread
    - `t.setDaemon(true);`

------

#### 1.5 Java Collections Framework (data structures)

- Collections Framework hierarchy
  - Iterable
  - Array
  - List
    - ArrayList
    - LinkedList
    - Vector
  - Set
    - HashSet
    - TreeSet
  - Queue
    - PriorityQueue
  - Map
    - HashMap
      - ConcurrentHashMap - threadsafe
    - HashTable
    - TreeMap
  - 
- data structure
  - internal structure
  - default_capacity
  - resize
  - threadsafe
- Iterator



115. what's Java Collections Framework?
     - Collection interfaces are divided into two groups, most basic interface are following two:
       - java.util.Collection
       - java.util.Map

- Map doesn't extends Collection interface, but it belongs to the **java Collections framework**.
  - different types:
    - Random Access
    - Ordered
    - Sorted
    - thread-safe

![](https://media.geeksforgeeks.org/wp-content/uploads/java-collection.jpg)

**Collection Hierarchy**



![](https://miro.medium.com/max/937/1*8xvUkJTWCF-gSIU0ywAjxA.png)

**Map Hierarchy**

![](https://4.bp.blogspot.com/-4FG1HxW0My4/WVjr8ftH0TI/AAAAAAAAAIA/_y876G2SqvcMF7tws-LVqSV5DhwWD943gCEwYBhgL/s640/map-interface-1.png)

116. what's iterable in java

     - implementing this interface will allow an object to be the target of the "for-each loop"

     ```java
     public interface Iterable<T>{
         Iterator<T> iterator();
         default void forEach(){}
         default Spliterator<T> spliterator(){}
     }
     
     ```

117. what's iterator in java

     - we can iterate the collection by iterator

     ```java
     public interface Iterator<E> {
         boolean hasNext();
         E next();
         default void remove(){}
         //...
     }
     
     ```

118. what's Array in java

     - it's a class
     - array is fixed size( need consecutive space, to ensure O(1) access time complexity)
     - array is fixed type
     - it's not threadsafe
     - since it's not threadsafe, its performance is kind of good

119. how to create array in java

     ```java
     int[] a = {1,2,3};
     int[] a = new int[4];
     
     ```

120. Are concrete classes in collection and Map are cloneable and serializable?

     - Basically, all the concrete classes in the Collection and Map are **cloneable and serializable**

121. what's Boxing/unboxing?

     - convert a primitive type value to its wrapper class's object

122. what's the difference of ArrayList and LinkedList

     | ArrayList                                                    | LinkedList                                                   |
     | ------------------------------------------------------------ | ------------------------------------------------------------ |
     | internally implement a **dynamic array** to store the element | internally use a **doubly linked list** to store the element |
     | better for **storing and accessing** the data,               | better for **manipulate the data** (insert, remove)          |
     | implements **List**  interface only                          | implements **List and Deque**                                |
     | manipulate(insert/remove) the data is **Slow**, need to shift the elements | manipulate the data is faster,                               |

123. ArrayList vs Vector

     - synchronization: 
       - vector is synchronized
       - arraylist is not
     - performance
       - since vector is synchronized so its performance is worse than arraylist
     - Growth rate
       - both of them internally implements object array to store the data. but the growth rate are different.
       - arraylist increments 50 % of current size
       - vector increments 100% of current size
     - traversal:
       - vector can be traversed by enumerator and iterator
       - arraylist can be traversed by iterator

124. what happens when we new an ArrayList and add an element to it

     - use Object[] to store the elements

     - DEFAULT_CAPACITY =10;

     - once we new an ArrayList

       - if we pass an initialCapacity into the constructor ,will create an Object Array with that capacity
       - if not, will assign an empty array to the elementData

     - once we add an element to the arraylist

       - it'll call ensureCapacityInternal(), 

         if DEFAULT_CAPACITY is larger than minCapacity, expand the capacity to 10

       - also resizing rate is 1.5 in arraylist

125. what's the default capacity of ArrayList

     DEFAULT_CAPACITY = 10;

126. What's the initial capacity of ArrayList

     - initial capacity is 0 if we don't pass min Capacity into the constructor
     - if we add first element into the arraylist, the capacity will expand to 10, which is DEFAULT_CAPACITY

127. what's the time complexity of add() method of ArrayList

     - since we need to copy the old elements into the new expanded array, 
     - the time complexity is O(n)

128. difference: with initial capacity and without

     ```java
     List list1 = new ArrayList();
     List list2 = new ArrayList(0);
     //elementData point to different EMPTY_ELEMENTDATA empty array
     list1.add(1);//list capacity is 10
     list2.add(1);//list capacity is 1
     
     ```

129. what's Map in java

     - Map is an interface in java

130. what's the difference between Map and List

     - Map is key-value pair structure, list is single value structure
     - map has no duplicate key

131. what's HashMap

     - DEFAULT_INTIAL_CAPACITY is 16
     - index =0 is kept by the map
     - internally is Array of Node

132. what happens when we put a key-value pair into map: `map.put("G",1);`

     - internally implement Node[] to store the element, Node<K, V> implements Map.Entry interface.
     - default initial capacity is 16
     - use key.hashCode() to calculate the hash for the key-value pair
     - create the node
     - use hash%(table.length-1) to locate the position
     - try to put node into the bin
     - if bin is empty/not found in the bin, 
       - no need to **resizing**(threshold decided by loadFactor), put the node into the bin
       - if require, resizing
     - if the bin is not empty
       - if the bin already has same key, use(==||equals) check whether the same, repalce the value only
       - else not the same key, kick the out node out, put the new node in, link it to the old node(form a linkedlist),
       - if the **linkedlist** is too long (TREEIFY_THRESHOLD=8), then convert the linkedlist to Red-Black tree, 
       - when reach the UNTREEIFY_THREASHOLD=6，convert to linkedlist

133. HashMap get(Object o) method

     - call the getNode() method
     - call the hash() method to get the hash of the key object, call the getNode() method
     - in getNode() method
       - first do null check of the Node[] and first node
         - if first Node's key ==|| equals() the passed in object, return the Node.value
         - else 
           - check wether it's instanceof TreeNode, search the object in the tree
           - if it's a linkedlist, iteratively check whether the object in the list

     ```java
        public V get(Object key) {
             Node<K,V> e;
             return (e = getNode(hash(key), key)) == null ? null : e.value;
         }
     
       
         final Node<K,V> getNode(int hash, Object key) {
             Node<K,V>[] tab; Node<K,V> first, e; int n; K k;
             if ((tab = table) != null && (n = tab.length) > 0 &&
                 (first = tab[(n - 1) & hash]) != null) {
                 if (first.hash == hash && // always check first node
                     ((k = first.key) == key || (key != null && key.equals(k))))
                     return first;
                 if ((e = first.next) != null) {
                     if (first instanceof TreeNode)
                         return ((TreeNode<K,V>)first).getTreeNode(hash, key);
                     do {
                         if (e.hash == hash &&
                             ((k = e.key) == key || (key != null && key.equals(k))))
                             return e;
                     } while ((e = e.next) != null);
                 }
             }
             return null;
         }
     
     ```

     

134. how to let get()-> O(1)

     - evenly distributed all the nodes(hashCode should be good enough)
     - loadFactor cannot be too small, or the threshold is too small. and we need to resize frequently, which is not good

135. what's HashMap DeadLock

     - two threads try to resize the HashMap at the same time, kind of like deadlock

136. what's the difference between **HashMap and HashTable**

     - HashTable is synchronized, whereas HashMap is not
       - HashTable is better for multithreading 
       - HashMap has better performance
     - HashTable does not allow null keys or values, HashMap allows one null key and any number of null valuess

137. what's **ConcurrentHashMap**

     - <1.7 ConcurrentHashMap use ReentrantLock on each bin/entry
     - after 1.8, ConcurrentHashMap remove that, it use **CAS(compare and sweap)** method and synchronized for concurrency,
     - when put an item
     - - if current bin is empty,       it'll use CAS to add
       - if current bin is not empty,       is either list or tree, it'll lock on the bin using synchronzied block       and add/update the bin
     - compare with previous, new one is much faster

138. what's **SynchronizedMap**

     - Collections.synchronizedMap()
     - wrapped the map methods with synchronized block

139. will HashMap keep insertion order

     - No, HashMap is not ordered or sorted
     - but, LinkedHashMap keep insertion order

140. HashMap vs ConcurrentHashMap vs SynchronizedHashMap

     - Synchronization

       - ConcurrentHashMap implements lock on each bin, 
       - while SynchronizedHashMap synchronize the whole map

     - Iterator

       - ConcurrentHashMap doesn't throw ConcurrentModificationException, so it is fail safe iterator
       - SynchronizedHashMap use fail fast iterator.

       

141. TreeMap 

     - keep sorted order, sorted by the key,
     - need to provide Comparator to TreeMap contructor

142. what's difference between Comparable and Comparator

     - Comparable<E>
       - is an interface, need to override compareTo() method
     - Comparator<E>
       - is also an interface
       - we need to override compare() method,
       - normally , we create anonymous inner class

     ```java
     // Comparable, compareTo()
     @Override
     public int compareTo(Cat cat) {
     	//positive, this>0
     	//0, this==o
     	//negative, this<o
     	
     	return this.weight-cat.weight;
     }
     
     // Comparator, compare()
     
     Comparator<Cat> c = new Comparator(){
     	@Override
     	public int compare(Object o1, Object o2){
     		return c1.weight-c2.weight;
     	}
     };
     
     ```

143. What's Set in java

     - an interface, extends Collection interface
     - not duplicated value

144. what's the relation of HashSet and HashMap

     - internally, HashSet use HashMap to implement, where the key in HashMap is the value in HashSet
     - every value put into the hashset will be put into a hashmap as key, 

145. how many kinds of iterators in java

     - there are two kinds of iterator
       - fail-fast iterator
         - if we fail, we get to know immediately
       - Fail-safe iterator

146. can we remove element from iterator?

     - we cannot remove the element before the iterator pointer reach the element
     - but we can remove the element after iterate it

147. java iterator is fail-fast iterator

     - while iteration by iterator, if the iterable has structural change at the place where it haven't been iterated, 
     - this iterator will throw ConcurrentModificationException

148. CopyOnWriteArrayList use fail-safe pattern

     - catch the exception, tolerance

149. how to loop through elements

     1. use traditional for loop
     2. use enhanced for loop
     3. use iterator
     4. use forEach() method

     ```java
     List<Integer> nums = new ArrayList<Integer>();
     // traditional for loop
     for(int i=0;i<nums.length;i++){
         
     }
     // enhanced for loop
     for(int i:nums){
         
     }
     // iterator
     Iterator<Integer> i = nums.iterator();
     while(i.hasNext()){
         System.out.println(i.next());
     }
     
     // forEach
     nums.forEach(e->System.out.println(e));
     
     // Map
     Map<Integer,Integer> map = new HashMap<>();
     
     // enhanced for loop
     for(Map.Entry<Integer,Integer> entry:map.entrySet()){
         System.out.println(entry.getKey());
         System.out.println(entry.getValue());
     }
     // iterator
     Set<Map.Entry<Integer,Integer>> entries = map.entrySet();
     Iterator<Map.Entry<Integer,Integer>> i = entries.iterator();
     while(i.hasNext()){
         System.out.println(i.next());
     }
     // forEach
     map.forEach((key,value)->{
         System.out.println(key+":"+value);
     });
     
     ```



------

#### 1.6 Java 8 



123. what's java 8 new feature

     - jvm change
       - meta space, move the perm gen out of jvm
     - interface
       - static/default method in interface(has function body)
     - learn JavaScript
       - **functional interface** + **lambda expression** to replace anonymous inner class
       - **Java Stream API**
     - forEach() method in Iterable interface

     

124. static / default method in interface

     - in java 8 we can have
       - public abstract (just like before)
       - public static (class level method, cannot be overridden)
       - public default method(object level method, can be overridden, has body)

125. why default methods in java 8

     - The default methods were introduced to provide backward compatility so that existing interfaces can use the lambda expression without implementing the methods in the implementation class.

126. functional interface

     - with annotation `@FunctionalInterface`
     - it's an interface with **only one abstract method**
     - no matter **how many static/default method**,
     - except an interface declares an abstract method overriding one of public methods of Object: toString(), hashCode(), equals()
     - like: Runnable, Callable, Comparator,

127. lambda expression

     - replace **anonymous implementation** of **functional interface**

     - expression

       ```java
       // Runnable
       Thread t = new Thread(()->{
           // code written in run() method
       });
       
       // Comaprator
       Arrays.sort(nums,(a, b) -> a.length() - b.length());
       
       ```

128. difference between **anonymous inner class vs lamba expression**

     - lambda expression is short form for anonymouss inner clas
     - but lamda expression is only used for funcitonal interface, but anonymous inner class can be used for multiple abstract method

129. difference between String, StringBuilder, StringBuffer

     - String is immutable class
     - StringBuilder is mutable, it's not heavy to manipulate string, performance is better
     - StringBuffer is threadsafe 

130. Stream API in java

     - Stream API **is used to process collections of objects**
     - a stream is sequence of objects that supports various methods which can be pipelined to produce desired result

131. Stream features

     - Stream is not a data structure instead it takes input from the Collections, Arrays
     - Stream don't change the original data structure, only provide the result as per the pipelined methods
     - each intermediate operation is lazily executed and return a stream as a result, hence intermediate operations can be pipelined,**Terminal operations** mark the end of the stream and return the result

132. different intermediate Operations

     - map: return a stream consisting of the results of applying the given function to the elements of this stream(one to one)

       ```java
       List nums = Arrays.asList(1,2,3);
       List square = nums.stream().map(x-<x*x).collect(Collectors.toList());
       
       ```

     - filter: filter the elements out Predicate return boolean

       ```java
       List res = nums.stream().filter(n-> n<2).collect(Collectors.toList());
       
       ```

     - sorted: use to sort the stream

       ```java
       List res = nums.stream().sorted().collect(Collectors.toList());
       
       ```

133. Stream API terminal operations

     - collect: return the result of intermediate operations

     - forEach: use to iterate through every element of the Stream

       ```java
       number.stream().map(x->x*x).forEach(y->System.out.println(y));
       
       ```

       

     - reduce: reduce the elements of a stream to a single value

       ```java
       int even = nums.stream().map(x->x*x).reduce(0,(ans,n)->ans+n);
       
       ```

       

       Stream API

       - Stream API provides functional approach to processing collections of objects
       - Non-terminal operations
         - filter
         - map
           - 
         - flatMap
           - if nested, move nested object out
         - distinct
           - remove duplicates
         - limit
           - limit the elements number
         - peek
           - return a new stream with all the elements
       - terminal operations
         - collect
         - forEach
         - reduce
         - min/max
         - count
         - anyMatch
         - allMatch
         - nonMatch
         - findAny
         - findFirst

134. what's singleton

     - in one scope
     - if I can only create only one object from the blueprint
     - then the blueprint is so called singleton

135. what's java singleton

     - in one jvm
     - can only create one object from one class

136. why we need singleton

     - some of the object is too large, only want to create once

137. how to create a singleton

     - private all constructors
     - create object in the class
     - have a `getInstance()` method return the created object

138. different kinds of singleton

     - eager singleton(always create the object)

       ```java
       public class EagerSingleton{
           private static final EagerSingleton instance = new EagerSingleton();
           private EagerSingleton(){}
           public static EagerSingleton getIntance(){
               return this.instance;
           }
       }
       
       ```

     - double-checked singleton(avoid multithreading problem)

       ```java
       class CheckedSingleton{
           private static volatile CheckedSingleton cs;
           private CheckedSingleton(){}
           
           public static CheckedSingleton getInstance(){
               if(cs==null){
                   synchronized(CheckedSingleton.class){
                       if(cs==null){//double check
                           cs = new CheckedSingleton();
                       }
              
                   }
               }
           }
       }
       
       ```

       - why volatile
       - The real problem is that `Thread A` **may assign a memory space** for `instance` before it is finished constructing `instance`. `Thread B` will **see that assignment and try to use it**. This results in `Thread B` failing because it is using a partially constructed version of `instance`.

     - lazy singleton

       - **private constructor**
       - **private static inner class** with **static final instance** created
       - **public static getInstance()** method

       ```java
       class LazySingleton{
           private LazySingleton(){}
           private static class A{
           	public static final LazySingleton ls = new LazySingleton();
           }
           public static LazySingletone getInstance(){
               return A.ls;// initialize A here
           }
       }
       
       ```

139. what's volatile in java

     - only when the value is changed, **force the value to writeback immediately**

       ```java
       volatile public int age;
       
       ```

     - avoid code rearrangement

### 2. JDBC, Hibernate

- JDBC
  - Connection Creation
  - 



1. what's JDBC

   - JDBC is short for **java database connection**
   - which is used to **connect the application with database**, only apply for Relational database
   - it's API package is java.sql

2. what information we need to connect the database with jdbc

   - database url
   - username
   - password
   - driver

3. how to use jdbc to connect the database

   ```java
   public class JdbcUtil{
       private static final String DRIVER = "oracle.jdbc.driver.OracleDriver";
   	private static final String URL = "jdbc:oracle:thin:@localhost:1521:XE";
   	private static final String USERNAME = "yushi";
   	private static final String PASSWORD = "mercury";
       
       public static Connection getConnection(){
           Connection conn = null;
           try{
               //load the class into perm gen
               Class.forName(DRIVER);
               conn = DriverManager.getConnection(URL,USERNAME,PASSWROD);
           }catch(Exception e){
               e.printStackTrace();
           }
           return conn;
       }
   }
   
   ```

4. Connection in JDBC

   - Connection is an interface which extends AutoCloseable

5. what's DAO in java

   - Data Access Object
   - declare only the basic database operations

6. how to save with JDBC

   ```java
   public void save(User user){
   	String sql = "{?=call SAVEUSER(?, ?)}";
   	try(Connection conn = JdbcUtil.getConnection();
       CallableStatement cs = conn.prepareCall(sql);   
       ){
           		cs.registerOutParameter(1,Types.INTEGER);
   			cs.setString(2, user.getName());
   			cs.setInt(3, user.getAge());
           cs.executeQuery();
       }catch(){}
   }
   
   ```

7. how to getAll 

   - ResultSet is a java representation of cursor(DB iterator)
   - next() is similar to hasNext()

   ```java
   public List<User> getAll(){
   	List<User> users = new ArrayList<>();
   	String sql = "select * from sample";
       
       try(Connection conn = JdbcUtil.getConnection();
           Statement st = conn.creatStatement();
           ResultSet rs = st.executeQuery(sql);
      	){
           			while(rs.next()) {
   				String name = rs.getString("name");//if int name, it'll try to convert the res to int
   				int age = rs.getInt("age");
   				User u = new User(name,age);
   				users.add(u);
   			}
       }catch(){}
   }
   
   ```

8. how to getByColumnName

   ```java
   public User getByName(String name){
       		User u = null;
   		String sql = "select * from sample where name = ?";//add ? as placeholder
       		try(Connection conn = JdbcUtil.getConnection();
   			PreparedStatement ps =conn.prepareStatement(sql);){
   			//place holder ? start from index 1
   			ps.setString(1, name);
   			ResultSet rs = ps.executeQuery();//this should be closed, but we didn't implement
   			if(rs.next()) {
   				u = new User(name,rs.getInt("age"));
   			}
   		}catch(Exception e) {
   			e.printStackTrace();
   		}
   		return u;
   }
   
   ```

9. what's the relationship of AutoCloseable, Connection, Statement(PreparedStatement, CallableStatement), ResultSet

   - Connection, Statement, ResultSet are interface, which extends AutoCloseable
   - CallableStatement extends PreparedStatement
   - PreparedStatement extends Statement

   ```java
   try(Connection conn = JdbcUtil.getConnection();
   Statement st = conn.createStatement();
   ResultSet rss = st.executeQuery(sql);){
       
   }
   PreparedStatement ps = conn.prepareStatement(sql);
   
   CallableStatement cs = prepareCall(sql);
   
   ```

   - PreparedStatement 
     - use place holder
     - can prevent sql injection
   - CallableStatement
     - once we have return, we have to use Callabletatement
   - ResultSet 
     - iterator like, java presentation of cursor

   ![](https://docstore.mik.ua/orelly/java-ent/servlet/figs/jsp_0902.gif)

10. JDBC commitment

    - **JDBC auto commit for each line**
    - connection.setAutoCommit(false);
    - connection.rollback();
    - we can manually unset the autocommit, jdbc will commit when connection is closed

11. what's Hibernate in java

    - Hibernate is a ORM tool
    - it's a java framework which simplifies the development of java application to interact with the database

12. what's ORM

    - ORM is **object relational mapping**
    - simplifies the data creation, manipulation, data access

13. how to use Hibernate

    - specify the mapping file for persistent class
      - `User.hbm.xml`
    - create the Configuration file
      - `hibernate.cfg.xml`
    - create Utility class
      - `HibernateUtil.java`
      - create a SessionFactory singleton
      - use ThreadLocal to ensure the thread safe and return copy of session
    - second level cache need configuration file
      - use ehcache
      - ehcache.xml

14. what's session in java

    - session is a space in jvm which store the data
    - session has a time line which is transaction
    - if ask session for a object
      - if doesn't have, it'll acquire the data from database
      - if has, will directly return the object
    - if set the object to another value, the object is attached status, it'll update the database when we commit the transaction
    - if set to the same value, won't change

15. Hibernate object status

    - transient state
      - not saved in the session
    - persistence(attached) state
      - saved to the session
    - detached state, 
      - after the session is closed

    ```java
    Session session = HibernateUtil.currentSession();
    Transaction t = session.beginTransaction();
    // transient state
    User tony = new User("Tony",123);
    //persistent state
    session.save(tony);
    tony.setAge(12);
    t.commit();
    HibernateUtil.closeSession();
    tony.setAge(10);//detached state
    
    ```

16. What' HQL

    - Hibernate query language

17. how many levels of cache in hibernate what are they

    - there can be two levels of cache
    - First level cache is session cache, once object is saved to the session, it is saved in session cache, which is attached state
    - second level cache is third party provided cache, like ehcache, session factory cache and query cache are located in second level cache

18. what's spring cache

    - spring cache is method level cache

19. Difference between get()  and load()

    - get() will retrieve the object immediately, which load() is lazy loading, load when use
    - get() return will be null if record not exist, load() will throw exception

20. what's load() method in hibernate

    - it's lazy loading
    - when we call load, the session will allocate an address to a fake proxy object
    - when we call getClass() method, it's public final method, cannot be overrdden, so the getClass() method is the proxy object's method, won't invoke creation of the User class
    - but when we call the method defined in the User class, it'll create the User class

    ```java
    		Session session = HibernateUtil.currentSession();
    		Transaction t = session.beginTransaction();
    
    		
    		User sherry = (User)session.get(User.class, "sherry");
    		User maggie = (User)session.load(User.class, "gao");
    		System.out.println("*************");
    		
    		System.out.println(sherry.getClass().getName());
    		System.out.println(maggie.getClass().getName());
    		System.out.println("*************");
    
    		System.out.println(sherry);
    		System.out.println(maggie);
    		
    		t.commit();
    		HibernateUtil.closeSession();
    
    ```



------

### 3. Web

- HTTP
  - version: 1.0, 1.1
  - structure: header, body
  - method: get, post, delete
  - status code: 1xx-3xx, 4xx,5xx
- web server
  - function
  - workflow
- servlet, jsp
  - servlet
  - jsp
- spring
  - IoC
    - Spring bean, spring bean container, spring scope
    - dependency injection, injection conflict
  - MVC
    - dispatcher servlet
    - jackson
    - workflow
  - Spring AOP
    - advice, PointCut, Aspect
    - weaving type
  - Spring transaction management
    - `@Tranactional()` annotation
    - Propagation level
  - spring boot
    - advantage
  - spring data jpa
  - Spring Cache
  - Spring Security
    - workflow



------



1. Basic Concepts

   - HTML : Hyper text markup language
   - css - cascading style sheet
   - http - hyper text transfer protocal
   - FTP - file transfer protocal

2. Client always send message to server to fetch the message from the server, response is the message fetched from the srever, server never send message to client

3. is HTTP request blocking

   yes, it's blocking

4. what's socket

   - it's software which connect the program to the port

5. what's web server/web application container

   - it's a software/container
   - which used to contain the web application
   - provide socket service, connect the program to the port, to enable the program to communicate
   - which is also a thread pool, each request come in, it'll generate a thread to deal with it
   - basically it's a giant jvm

6. describe the workflow of web server

   - the listener of web server on certain port like 8080 detect the request
   - the server will **create an thread to deal with the request**
   - the thread create response
   - web application will fill in the response
   - once finished, client retrieves the response back

7. web servers

   - tomcat
   - jboss
   - weblogic

8. status code of request

   five kinds:

   - 1xx - 3xx, good
   - 4xx , client issue
   - 5xx, server issue

9. tomcat

   - web server host by apache
   - can deploy war (web archive) file on tomcat
   - we can deploy multiple application on the tomcat

10. can browser send all kind of request

    - browser url bar can only send get request
    - but we can send all kind of requests based on the requested page we defined in it

11. Browser component

    - url bar
    - body
    - menu

12. what's the format of http request

    - HTTP header
      - key-value pair (string)
      - url, method, content-type
    - HTTP Body
      - body
        - string(plain text, xml, json)
        - file

13. what's json

    - it's javascript object notation
    - kind of like javascipt object

14. what's web service

    - it's the way web server provide web service
    - SOAP
      - stands for Simple object access protocol
      - safer than rest
    - REST
      - stands for **Representational state transfer**
      - can accept all the http methods( get/post/delete)

15. what's the version of HTTP

    - HTTP/1.0 only has service()
      - its life cycle is inti(), service(), destroy()
    - HTTP/1.1
      - add more method: post, get,...

16. what's servlet

    - servlet is java software component
    - which is used to **handle http request**
    - any classes which **extends HTTPServlet** can be called as servlet

17. what does servlet do

    - in Java only servlet can receive http request

18. how does servlet deal with the http request

    - tomcat create the thread
    - thread create the request/response object, fill in the request object
    - pass the request and response object to servlet
    - servlet fill in the blank response

19. what's servlet life cylcle?

    - init()
    - service()
    - destroy()
    - we can only have **doGet/doPost...**

20. how to get parameters from url

    - `String name = request.getParameter("name");`

21. web.xml

    - we define the servlet and url-servlet mapping,
    - data source, 
    - filter

22. what's filter in web.xml

    - use filter to check the privilege(username, password, right before the srevlet)
    - use multiple filters in a chain to filter, design pattern, chain of responsibility

23. what's jsp

    - it's java server page
    - it's a collection of technology with which can **dynamically generate the web pages**

24. what's form in jsp

    - form is basic unit to send info to backend in jsp

25. difference between forward and redirect

    - forward is like you have a phone call to some one's house, his wife pick up the phone, and he is in the shower, you talk to his wife and let his wife tell the things to him
    - redirect is like he is available right now, and his wife give the phone to him to answer the phone

26. jsp life cycle 

    similar to servlet

    - jsp init()
    - jsp servlet
    - jsp destroy()

27. what's jsp bean scope

    - page
      - bean only accessible by the page
    - request
      - request can forward, many page can access the bean
    - session
      - stored in the server
    - appliaction
      - one tomcat, beans can be access by only application

28. difference between GET/POST

    - GET response has no body(server ignored the body)
    - Post request is more secure, which hide the information from the url

29. can we handle different url in one servlet

    - yes, 
    - like the annotation,
      - @WebServlet({"/ms","/rs"})

30. web.xml vs annotation

    - annotation is more convenient

31. what's Spring IoC

    - it's short for inversion of control
    - which means,  we can **hand over the control of beans to spring**, let spring inject the dependency for us

32. What's Spring bean container

    - this bean is singleton

    - used to store id-class pairs, which are spring beans

      ```xml
      <bean id="ud" class="c.mercury.daos.ud">
      
      ```

      

    - call configuration file to create ApplicationContext object

      ```java
      ApplicationContext actx = new FileSystemXmlApplicationContext("resources/spring-config.xml");
      
      ```

    - call getBean("id") to get the bean

    ```java
    		//new the spring container
    		ApplicationContext actx = new FileSystemXmlApplicationContext("resources/spring-config.xml");
    		
    		System.out.println("*********************");
    		//the 
    		UserDao ud = (UserDao) actx.getBean("ud");
    
    		UserDao ud2 = (UserDao) actx.getBean("ud");
    
    		System.out.println(ud==ud2);//true, we get the same address
    		
    		UserDao udCopy = (UserDao) actx.getBean("udCopy");
    
    		System.out.println(ud==udCopy);//false, different bean
    
    		System.out.println("*********************");
    		//spring applicationContext new bean with constructor with parameters
    
    		UserDao udWithParameter = (UserDao) actx.getBean("udWithParameter");
     
    		System.out.println(udWithParameter);
    
    		System.out.println("*********************");
    
    		RegistrationService rs = (RegistrationService)actx.getBean("rs");
    		System.out.println(rs);
    
    		System.out.println("**********prototype***********");
    		RoomDao rd = (RoomDao)actx.getBean("rd");
    		RoomDao rd2 = (RoomDao)actx.getBean("rd");
    		System.out.println(rd==rd2);
    
    
    ```

33. what's spring bean

    - <k,v>, id-object pair is spring bean

    - ```java
      <bean id="ud" class="c.mercury.ud">
      
      ```

    

34. singleton

    - in one scope, one blueprint can only have one object
    - java singleton
      - in jvm, one class can only have one object
    - spring singleton
      - in one ApplicationContext(spring bean container), one bean can have one object

35. Spring scope

    - singleton
    - prototype
      - getBean()/ref/autowire, will create  new object
    - request
    - session
    - global session(remove after spring 5)

36. how does spring implement IoC

    - Dependency injection

37. how to add spring project jar beans into my own container

    - use component scan

38. dependency injection conflict(if type is an interface, and two beans both implements that interface, inject which)

    1. change field name to match the bean's name
    2. add @Primary to the class
    3. add @Qualifier("beanName") under the @Autowired

    - 3 > 2 > 1

39. Spring MVC

    - Spring mvc is a java framework which is used to build web applications
    - MVC is a design pattern, not GoF 23
      - model, data and logic structure
      - view , web page display the model
      - controller

40. what's dispatcher servlet

    - spring create servlet for us including dispatcher servlet
    - contain an ApplicationContext
    - all the requests (url) will be received by dispatcher servlet(only servlet can receive request in java)
    - based on the following sub uri to find the controller(based on the annotation)

41. jackson

    - json convertor
    - we can add converter in the spring-mvc-servlet.xml

42. what's REST

    - representational state transfer

43. what's RESTful

    - using Beans name as controller's uri
    - @RequestMapping("/users")

44. Difference between **@Controller vs @RestController**

    - Traditional MVC controller relies on the View technology, while RESTful controller simply return the object and the data is directly written to the HTTP response
    - @ResponseBody annotation: added in front of the method
      - Traditional MVC controller will return ModelAndView object
      - convert the return value and write it to the HTTP response automatically
    - @RestController = @Controller + @ResponseBody

45. what's spring boot

    - java-based framework
    - used to **build stand-alone spring application**
    - which **solve the maven dependency conflict problem**
    - and **each application has an embedded tomcat server**

46. how does spring boot do component scan without web.xml

    - component scan will automatically scan the package specified when we initialized the project

47. jar vs war

    - war can be deployed on the tomcat
    - jar can be directly execute
      - java -jar HW.jar

48. what's mockito

    - it's kind of embedded database use to test the dao layer

49. what's jpa

    - it's short for java persistence API
    - which is kind of a specification
    - Hibernate and spring data jpa both implement the jpa

50. what's spring data jpa

    - It's a part of spring framework
    - which implements JPA specification including JDBC connection and object-relational mapping
    - on top of that, if we implements JpaRepository, it'll generate database queries from method names for us

51. how many injections in spring

    - constructor injection
    - setter injection (**need no-arg constructor**)
    - field injection(bean injection, through reflection)

52. create dao interface which extends JpaRepository<EntitydClass, IdClass>

53. how does JSON converter work

    - call all the getter to convert the json into java object

54. how does @JsonIgnore work

    - added before the setter, the field will be ignore when convert the json into object
    - added before getter, convert object to json, will ignore the field
    - when added before field, always ignore

55. log

    - in tomcat, all the console logs will be output into catalina.out

56. log4j

    - short for log for java
    - slf4j, wrap the log4j

57. log4j importance level - 7

    - None(print nothing)
    - Fatal
    - Error
    - Warn
    - Info
    - Debug
    - Trace

58. how to use log4j

    - configure the slf4j in application.properties

      ```yml
      logging.file=SpringBootRestDemo.log
      logging.level.root=INFO
      
      ```

    - ```java
      private Logger logger = LoggerFactory.getLogger(this.getClass());
      
      logger.debug("ssth");
      logger.trace("sth");
      
      ```

59. what's AOP

    - Aspect of programming
    - when/where/what
    - provide additional functionalities without changing the code
    - like constructor

60. in spring how to use AOP

    - @Component
    - @Aspect ---> to mark as AOP class

61. Spring AOP

    - when--> advice

      - five advices

      - @Around = @Before+@After

      - @After = @AfterReturning

        +@AfterThrowing

    - where-->Pointcut()

    - what---> Aspect

62. how many **AOP weaving types**

    - there are three types
      - compile time
      - class loading time
      - runtime

63. spring transaction management

    - if the method catch exception, it'll rollback
      - we still see the exception
    - if the method finished, it will commit
    - use **@Transactional()** annotation

64. propagation level

    - can have nested transaction
    - 1
    - {
      - 3
    - }
    - 2

65. rollback only works on its own transaction

    - 3 will only roll back itself

66. Propagation level

    - Propagation.REQUIRED
      - if exist a transaction, use the old 
      - otherwise, create a new one
    - Propagation.REQUIRES_NEW
      - create a new one
    - Propagation.MANDATORY
    - Propagation.NEVER
    - Propagation.NESTED

67. what's spring cache

    - it's function level cache
    - if stateless function is always getting called and running very slow, enable  caching logic on it to cache the result
    - it's a Map<Object, Object> in jvm
    - if find the key in the map, directly return the value

68. how to use spring cache

    - ADD dependency in pom.xml
    - ADD @EnableCaching before the main class
    - add annotation over the slow function
      - @Cacheable("abc")

69. how many annotation mark as bean

    - there are four
      - @Component
      - @Repository
      - @Service
      - @Controller/@RestController

70. What's spring security

    - spring security is kind of a java framework that provide authenticaiton, authorization and other security feature to the applications
    - it is filter based, like filter in servlet

71. how to implement spring security

    - Bean layers
      - Profile should
        - implements GrandedAuthority(), 
        - override getAuthority() method
      - User should 
        - implements UserDetails, 
        - override 5 methods 
    - Dao Layer
      - UserDao
        - add `public User findByUsername(String username);`
    - Service layer
      - UserDetailsServiceImpl
        - implements UserDetailsService
        - override loadUserByUsername()
    - Config 
      - create SecurityConfig
        - extends `WebSecurityConfigurerAdapter`
        - override `configure(HttpSecurity http)` method
        - add annotation `@EableWebSecurity` and `@EnableGlobalMethodSecurity(prePostEnabled =true)`
        - autowire the `UserDetailsServiceImpl `

    ```java
    	public void configure(HttpSecurity http) throws Exception {
            http
                .cors()
                .and()
                .csrf().disable()
                .authorizeRequests()
                .antMatchers().permitAll()
                .antMatchers().hasRole("ADMIN")
                .antMatchers().hasAuthority("ROLE_ADMIN")
                .anyRequest().authenticated()
                .and()
                .formLogin()
                .usernameParameter("username")
                .passwordParameter("password")
                .httpBasic();
            
        }
    
    ```

72. Spring security work flow

    1. check the username whether exist
       - if not, return error
    2. if exist username, decode the password,
       - call `UserDetailsServiceImpl` to get the user's password
    3. check the password
       - if not the same, return error
       - if the same, send back response with JSessionId

73. what's SOP

    - same orgin policy

74. what's cors

    - cross-origin resource sharing
    - we should add AllowedOrigin

75. what's csrf

    - cross site request forgery
    - add the toke

76. workflow of spring mvc

    - A request goes through      DispatcherServlet,
    - use @Controller to find a      controller class
    - use @RequestMapping to find      the corresponding emthod to handle the request
    - then the method returns a      ModelAndView object to DispatcherServlet, in which model contains data and      view contains a string that will be converted to a real url by      ViewResolver
    - DispatcherServlet send the      view object to the ViewResolver to get the actual view page
    - Finally dispatcherServlet      will pass the Model object to the view page to display the result and      fulfil the reponse body and send it back

------



### 4. Microservices





1. what's message queue

   - a queue of message sent between application
   - can implement publisher-subscribeer, producer-consumer
   - activeMQ, redis
   - kafka

2. What's JMS

   - short for java message service
   - is a java message-oriented middleware api for sending messages between applications,
   - which is an implementation to handle producer-consumer problem

3. How to use ActiveMQ in java

   1. start the activemq application

      ```
      1. in command line, cd to ActiveMQ /bin folder
      2. in command line, execute : activemq start
      3. http://localhost:8161, log in
      	username: admin
      	password: admin
      
      ```

   2. add the dependency of activemq to the spring boot applications

      ```xml
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-activemq</artifactId>
      </dependency>
      
      ```

   3. Producer

      ```java
      Component
      public class OrderInfoProducer {
      	
      	@Autowired
      	private JmsTemplate jmsQueueTemplate;
      	
      //	autowire by name
      //	@Autowired
      //	private JmsTemplete jmsTopicTemplate;
      	
      	public void sendOrderForReport(int oid) {
      		// hardcode
      		OrderInfo oi = new OrderInfo();
      		oi.setId(oid);
      		oi.setQty(222);
      		oi.setProductId(123);
      		
      		jmsQueueTemplate.send("OrderReport", new MessageCreator() {
      			@Override
      			public Message createMessage(Session session) throws JMSException {
      				return session.createObjectMessage((Serializable)oi);
      			}
      		});
      		
      	}
      }
      
      ```

   4. Consumer

      ```java
      @Component
      public class OrderInfoConsumer {
      	
      	// use spring jms, it'll enable the annoataion, or use java jms will have to use xml to configure
      	// destination is the message queue name in the activemq
      	// the is the function triggered by the event
      	@JmsListener(destination = "OrderReport", containerFactory = "orderInfoListener")
      	public void receive(Message msg) throws JMSException {
      		System.out.println("********  Getting MSG  ***********");
      		System.out.println(msg);
      		ObjectMessage objectMessage = (ObjectMessage) msg;
      		OrderInfo orderInfo = (OrderInfo) objectMessage.getObject();	// deserialize
      		System.out.println(orderInfo);
      	}
      	
      }
      
      ```

4. what is spring cloud 

   - a framework to build robost cloud application
   - provide tools to build distributed system

5. techniques

   - Ribbon, 
     - implement load balancing
   - zuul
     - monitor the status of service server
   - eureka
     - registry service,
     - store the IP/port of the service servers
   - Hystrix
     - circuit break, when load is to heavy
   - Feign
     - send request to other micro service to call the dao, using RestTemplate

------

### 4. SQL

#### Overview

- Table
  - Normalization and Denormalization
  - DDL(create , drop, alter table)
  - Column, pk & fk, constraint, view
- Row operation 
  - CRUD
    - create, read, update, delete
  - Compound operations
    - join, union, group by, sub query
- Function, stored procedure, triggers
- Flow control & performance tuning
  - Transaction
  - index

#### Details

1. What's SQL

   - short for Structured Query Language
   - used for storing, manipulating and retrieving data in database

2. what's relational database

   - a collection of relations of two-dimensional tables

3. types of relationship

   - One to One
   - One to Many
   - Many to Many

4. Normalization

   - break a big table into small tables to reduce the data redundancy

5. Denormalization

   - join small tables into a big table to improve the performance

6. Normalization forms

   - 1NF
   - 2NF
   - 3NF
   - BCNF

7. Oracle data types

   - VARCHAR2(size) : variable-length character data
   - CHAR(size) : fixed-length character data
   - NUMBER(p,s) : variable-length numeric data
   - DATE : date and time values
   - LONG : variable-length character data <2 GB
   - CLOB : single-byte character data < 4GB

8. DDL

   - create : 

     `CREATE TABLE table_name ( column_name column_type,...);`

     ```sql
     CREATE TABLE Employee (
     	ID int NOT NULL,
         name varchar2(100)
     );
     describe Employee
     
     ```

   - truncate : delete the records

     ```sql
     TRUNCATE TABLE Employee CASCADE;
     
     ```

   - drop :  delete the table

     ```sql
     DROP TABLE Employee;
     
     ```

   - alter : alter table Column

     - column name

       ```sql
       ALTER TABLE Employee RENAME
       COLUMN name TO username;
       
       ```

     - add column

       ```sql
       ALTER TABLE Employee
       ADD age number(2,3);
       
       ```

     - drop column

       ```sql
       ALTER TABLE Employee
       DROP COLUMN age;
       
       ```

     - modify column type

       ```sql
       ALTER TABLE Employee
       MODIFY username varchar2(150);
       
       ```

   - Multiple modification

     ```sql
     ALTER TABLE Employee
     MODIFY (
     	name varchar2(100),
         gender char(6);
     )
     ADD (
     	address varchar2(100);
     );
     
     ```

9. types of contraints

   - NOT NULL
   - UNIQUE
   - PRIMARY KEY
   - FOREIGN KEY
   - CHECK

10. what's constraint

    - constraint enforce rules at the table level
    - prevent deletion of a table if there are dependencies(foreign key)

11. different types of keys

    - primary key
      - uniquely determines a row and it does not allow null value
    - foreign key
      - defined on a column of the child table and it refers to a primary key of parent table

12. how to create a constraint to a table

    - in the table creation
    - after table creation

    ```sql
    create table dept (
    	deptno number(2),
        dname varchar2(14),
        CONSTRAINT dept_dname_uk UNIQUE (dname),
        CONSTRAINT dept_deptno_pk PRIMARY KEY (deptno)
    );
    
    ```

    - foreign key

    ```sql
    create table emp (
    	empno number(4)
        deptno number(7,2) NOT NULL,
        CONSTRAINT emp_deptno_fk FOREIGN KEY (deptno) REFERENCE dept (deptno)
    );
    
    ```

    - check

    ```sql
    CONSTRAINT emp_deptno_ck CHECK (deptno between 10 and 99)
    
    ```

    

13. DML , CRUD - create, read, update, delete

    - insert into ...values...
    - update ... set ... where ...
    - select ... from ... where ...
    - delete from ... where ...

------

### 5. JavaScript

#### 5.1 data type

1. what's javascript

   - javascript is not OOP languages, it's procedure oriented language like C
   - it's weakly typing language, we can reassign the type of variable
   - ES5 does not have class, just simulate it

2. some basic operation

   - console.log();
   - require()
     - import another file
   - typeof
     - check the type of variable

3. Data types

   - primitive type(3+2), 3 with value, 2 without value
     - number(NaN, Infinity)
     - string
     - boolean
     - null(manually assigned, indicate no value, type is object)
     - undefined(automatically assigned)
     - Symbol(ES6)
   - reference type
     - array(array is an object), object

4. variable declaration

   - use var to declare local variable

     - ```javascript
       var s ='stupid';
       
       ```

   - without var, it'll declare global vaiable

     - ```javascript
       s = 'stupid';
       
       ```

5. type check

   - use typeof
     - typeof undefined =>undefined
     - typeof null => object
     - typeof NaN => number
     - typeof [1,2,3] => object
   - special check
     - isNaN(NaN)
     - Array.isArray([1,2,3])

6. equality check

   - ==, equality check
     - different type will convert type
     - will compare value
   - ===, strictly equality check
     - type check , then value
     - both reference types, only check value
   - undefined == null -> true
   - undefined === null -> false

7. falsy value

   - false
   - 0
   - '' -> empty string
   - null
   - undefined
   - NaN

8. how to create object in javascript ES5

   - object literal
     - var o1={name:'bob'}
   - object constructor function, use new
     - var o2 = new Object();

9. how to create array

   - use [] notatin
     - var a1 = [1,2,'a'];
   - use constructor
     - var a = new Array();

10. how to access the array

    - access with index
      - a[0]

#### 5.2 function & scope & hoisting

11. what function in javascript

    - reusable code block
    - can has parameters
      - function foo(a,b){}
    - can has return, but don't have to ,
      - will automatically add `return;`, which is `undefined`

12. function declaration

    - regular
      - function foo(){}
    - anonymous
      - var foo = function(){};

13. how to invoke the function

    - use () notation
      - foo();

14. we can have nested function

    - ```javascript
      function outer(){
          function inner(){
              
          }
      }
      
      ```

15. variable scope

    - scope is restrict where a variable can be used
    - function local scope(nested) < file scope < global scope
    - var can be used to declare function/file scope variable
    - without var is declaring global scope variable, which is same to add an property to global object

16. variable search chain

    - when we try to access a variable, js will try to search for in a chain
    - current local scope->outer(function/file) scope -> global scope -> not defined error

17. what's hoisting

    - before javascript executing, js will run a hoisting process
      - it'll scan all the definitions of variables/functions of current scope
      - it'll **move declarations** of all the variables/functions **to the top of current scope(function/file)**
      - the **assignment will stay where they are**

18. variable hoisting

    ```javascript
    console.log(n);//undefined
    var n=1;
    
    ```

19. function hoisting

    - regular function definition will be hoisted to the top entirely
    - anonymous function will only hoist the var declaration

    ```javascript
    // regular function hoisting
    bar();
    function bar(){
        console.log("bar");
    }
    
    // anonymous function hoisting
    foo();// error: foo is not a function
    var foo = function(){
        console.log("foo");
    }
    
    ```

20. ES6 hoisting

    - in ES6 let and const can be hoisted, but before the assignment cannot access the variable, or it'll throw ReferenceError

    ```javascript
    console.log(x);	//ReferenceError
    let x = 1;
    
    ```

    

#### 5.3 Object & this

20. two ways to declare object

    - use object literal

      ```javascript
      var bob = {
          name:'bob',
          age:20,
          'last name':'Li',
          'primary-address':'princeton'
      };
      
      ```

    - use constructor function

21. how to access object property

    - dot notation: simple word property, cannot access numeric property(like array)
      - bob.id
      - bob.last name ==>wrong
      - bob.0 ==>wrong
    - bracket notation, can access any property
      - bob['last name'];
    - if not exist, return **undefined**

22. add/update property

    - if not exist, add property when assign
      - `bob.id =1;`
    - if exist, update the value of property when assign
      - `bob['last name']=boby;`

23. how to use constructor to create object

    - use constructor function to simulate a class

    ```javascript
    function Student(name,age){
        this.name = name;
        this.age = age;
    }
    
    ```

24. what happens when we call new to create an object

    - js will create an empty Student object
    - resolve parameters in the function: 
      - declare parameters
      - assign the values(like ;)
        - var name='bob'
        - this.__ prototype __ = Student.prototype
      - this will refer to the empty object's address
      - add property/value pairs to this(new created object)
      - return the object

25. different ways to call constructor function will cause different this

    - call new to create an object
      - this-> newly created object
    - call it as regular function
      - this -> the caller of the function
      - caller is the whole left part that invoke the function, if nothing in the left, this->global

26. global caller

    ```javascript
    function Student(name, age){
    	this.name = name;
    	this.age = age;
    }
    var s1 = Student('alex',30);	//call it as function
    console.log(s1);			//undefined
    console.log(name);		//'alex'
    console.log(age);			//30
    // this of s1 will refer to the global object, name and age will be set to global
    
    ```

27. object's function

    ```javascript
    var alice = {
    	name : 'Alice',
    	age : 40,
    	print : function(){
    		console.log(name, age);
    	},
    	printThis : function(){
    		console.log(this.name, this.age);
    	}
    	
    };
    
    alice.printThis();//'Alice', 40
    alice.print();       // not defined error, class is not scope
    
    ```

28. scope in object

    - object has no scope, only function can create a scope
    - function in the class has scope

29. difference between this.price & price

    - this.price is property, if not exist, got undefined
      - if caller is function, function is also object, search chain is prototype chain
    - price is variable, if not exist, got not defined error
      - search chain is variable scope chain, object has no scope

30. how to change the binding of this in javascript

    - call():
      - first parameter should be address of this(object variable)
    - apply():
      - first parameter is like call(), should be the address of this, use an array to contain all the parameters to pass into the function
    - bind():
      - pas object address and return a new function
    - invokation
      - `foo.call(objectVar, param1,...)`
      - `foo.apply(objectVar,[param1,...])`
      - `var newFoo = foo.bind(objectVar);`

    ```javascript
    function foo(){
        console.log(this);
    }
    foo1();//global
    var f = new foo();//object
    foo.call(f);//foo
    
    ```

31. Object object properties

    - Object.keys()
      - internal structure of array, for in loop
    - Object.defineProperties()
      - value, enumerable, writable
    - Object status, extensible, sealed, frozen

32. two ways to print all properties of an object

    - use Object.keys() to get all the keys
    - use for in loop

33. for-in loop in javascript

    - for in loop, won't create a scope
    - key is file scope level variable
    - if without var, key is global scope variable

    ```javascript
    for(var key in bob) {
        console.log(key+':'+bob[key]);
    }
    
    ```

34. array internal structure

    - array internally is an object, typeof [1,2,3] ==> object
    - Object.keys(arr) can only get numeric property, cannot get length
    - arr.length, length property can be access by dot notation

35. how to make property invisible to Object.keys()/ for in loop(like length in array)

    - create property as a non-enumerable property

    ```javascript
    var bob={name:'bob'};
    Object.defineProperty(bob,'salary',{
        value:1000,
        enumerable:fale,
        writable:true//value can be changed
    });
    
    ```

36. Object status

    - extensible:
      - can add new property to an object
        - `Object.isExtensible(obj);`
        - `Object.preventExtensible(obj);`
    - sealed:
      - prevent to add/delete property of an object
        - `Object.seal(obj);`
    - frozen:
      - prevent add/delete/update property of objct
        - `Object.freeze(obj);`

37. what's closure in javascript

    - closure is the combination of a function enclosed with reference to its surrounding state
    - it gives us access to an outer function's scope from an inner function

38. how to generate a closure, necessary condition

    - inner+outer function, return inner function
    - outer variables used in inner function
    - after execution of outer function, will create a closure

39. pros and cons

    - advantage: avoid creating global variables
    - disadvantage: never be garbage collected, will cause memory leak

40. Closure example

    ```javascript
    function increaseFactory(){
        var a =1;
        function increate(){
            console.log(a++);
        }
        return increase;
    }
    var increase = increaseFactory();
    increase();	//1
    increase(); //2
    //...
    
    ```

41. self-invoke function/IIFE(immediate invoke function expression)

    - use ()() double parenthesis implementation
    - first () contains the anonymous function, second () invoke the function

    ```javascript
    (function(){
        console.log(`I'm stupid`);
    })();
    
    ```

42. advantages of self-invoke function

    - singleton
      - ensure that we can only have one function
    - encapsulation
      - like private field(using closure), getter, setter  in java

    ```javascript
    var counter = (function(){
        var count =0;
        return {
            getCount:function(){
                return count;
            },
            setCount:function(c){
                count = c;
            }
        };
    })();
    
    console.log(counter.getCount());
    counter.setCount(10);
    
    ```

43. what's prototype in javascript

    - prototype is an object
    - any js function has a prototype property, which points to an object
    - objects created from the constructor function can access everything in the prototype object
    - in other words, we use prototype object to declare some data shared among all the instances of constructor function

44. what's __ proto__ in javascript

    - it's internal private system reserved variable
    - every javascript object has this property, which points to its constructor's prototype object

45. what's difference between prototype and __ proto__,

    - prototype is in the constructor function ,which points to an object
    - __ proto__ is in the object, which points to the constructor's prototype

46. how to assign a prototype

    ```javascript
    var A = new Function();//every function is instance of Function object
    A.prototype = new Object();
    A.x =1;
    A.prototype.getX = function(){
        return this.x;
    }
    
    ```

47. How to implement inheritance in javascript

    ```javascript
    function Parent(){
        this.x =1;
    }
    Parent.prototype.getX = function(){
        return this.x;
    }
    function Child(){
        this.y = 2;
    }
    var p = new Parent();
    Child.prototype=p;
    
    // original: c -> Child.prototype -> Object.prototype -> null
    // reassign: c -> Child.prototype(p) -> Parent.prototype -> Object.prototype -> null
    var c  = new Child();
    console.log(c.y);		//2
    console.log(c.x);		//1
    console.log(c.getX());	//1
    
    console.log(c.constructor);		// should be Child, but is Parent
    
    
    ```

48. The Inheritance about have one problem, that is  the constructor of c is Parent, not Child

    - only through new constructor can add __ proto__ and constructor property to the object

    ```javascript
    function Student(){}
    var s = new Student();
    // during the new process
    s.__proto__ = Student.prototype;
    Student.prototype.constructor = Student;
    s.__proto__.constructor => Student;
    
    ```

49. another way to Inheritance, **solving the constructor problem**

    ```javascript
    function Super(){
        this.x = 1;
    }
    Super.prototype.getX = function(){
        return this.x;
    }
    function Sub(){
        Super.call(this);
        this.y = 2;
    }
    Sub.prototype = Object.create(Super.prototype);
    Sub.prototype.constructor = Sub;
    
    var sub  = new Sub();	// 1. create {}, 2. var, 3. this ->{},  
    
    console.log(sub.x);
    console.log(sub.y);
    console.log(sub.getX());
    
    ```

50. two ways to Inheritance

    - first
      - use object created from the Parent constructor function as prototype of the Child constructor function
      - constructor will be the Parent Constructor
    - second one
      - assign prototype of Parent constructor function as Child constructor's prototype, no need to create new object
      - we can assign the constructor in the Parent's prototype?

51. asynchronous operation

    - javascript is running in a single thread, 
    - doesn't support multi-threading
    - asynchronous codes will be executed after all the sync codes are finished
    - if sync code aren't finished, like infinite loop, the async code won't be executed

52. asynchronous functions

    - setTimeout()
    - setInterval()

    ```javascript
    setTimeout(function(){},3000);
    setInterval(function(){},2000);
    
    ```

    - these two function will return a number as id, which can be used to clear the asynchronous method

    ```javascript
    var it = setInterval(function(){},1000);
    setTimeout(function(){
        clearInterval(it);
    },5000);
    
    ```

53. what's event loop in javascript

    - javascript use **stack** to execute the synchronous operations, **one thread**, only has **one stack**
    - use **Web API Pool** to register the asynchronous functions
    - setTimeout() is synchronous function, but the anonymous function inside it is the asynchronous function
    - setTimeout() **register** the asynchronous function inside the web api pool, set a timer to the anonymous function, 
    - once the asynchronous function timer is timeout, move the asynchronous function to the **queue**
    - use **queue** to contain the timed out asynchronous function
    - when the stack is empty, will put the head of queue into the stack to execute
    - once previous head of queue executed, it'll pop out new head of queue and push it into the stack

54. use for loop and closure to print i out every 1s

    ```javascript
    for(var i=0;i<5;i++) {
        setTimeout((function(i){
            return function(){
                console.log(i);
            }
        })(i),1000);
    }
    
    ```

55. Promise is ES6 feature

    - used to solve the callback hell
    - nested asynchronous function will lead to callback hell

56. what's promise

    - promise is an object which is used to wrap and execute asynchronous operations
    - promise has **three status**
      - pending (while async op is running)
      - resolved (use resolve() method after async op finishes successfully, set promise to resolved status)
      - rejected (use reject() method, after async op finished unsuccessfully, set promise to rejected status)

    ```javascript
    var promise = new Promise(function(resolve, reject){
        setTimeout(function(){
            if(Math.random()>0.5){
                console.log();
                resolve();
            }else{
                console.log();
                reject();
            }
        },2000);
    });
    
    ```

    - after promise is created, we can register two callback function to handle async operation based on promise status

    ```javascript
    promise.then(function(){
        //call back succeed
    },function(){
        // callback fail
    });
    
    ```

    - use chaining to register multiple callback functions

    ```javascript
    promise.then().then();
    
    ```

    - in jQuery is a promise

    ```javascript
    $.get('http://www.baidu.com').then(
    	function(data){
            
        },function(err){
            
        }
    );
    
    ```

57. jQuery

    jQuery is kind of a javascript library, which can simplify operations in javascript like :AJAX call and DOM manipulation, css manipulation, event methods

58. two ways to execute jQuery code after DOM objects are created

    1. `window.onload = function(){};`
    2. `$(document).ready(function(){});`

59. syntax of jQuery

    ```javascript
    $('selector').method();
    
    ```

60. different kinds of selector

    - single
      - element(use element tag): $('p')
      - id(use #, pound/hash): $('#id')
      - class(use . , dot): $('.class')
      - attribute(use [], brackets): $('[href="http:"]')
        - start with [href^="https"]
        - end with [href $= ".edu"]
        - contains [href*="google"]
    - dom relation
      - child(use >, greater than sign): $('div>ul')
      - descendent(use space): $('div ul')
    - logic
      - combined/or (use , comma)： $('a, p')
      - join/and (use nothing between): ${'p.fontsize'}
    - pseudo use (:, colon)
      - regular pseudo
        - $('ul li : first')
        - $('ul li : last')
        - $('ul li : even') //odd
      - pseudo nth-child
        - $('ul li : nth-child(3n)') //3,6,9
      - pseudo nth-of-type
        - $('ul li : nth-of-type(3)')

61. how does nth-child selector work

    - search all child elements, find the nth one, check if it is certain selector
      - if yes, return that element
      - if no, return null
    - first select, then check

62. how does nth-of-type() work

    - select all the certain selector out, then return the nth one
    - first check, then select

63. what does jQuery method do

    - add/remove/change the element/attribute/css, 
    - react to the event

64. list of jQuery methods

    - handle the event
      - $('selector').on('click',function(){});
    - add element
      - $().append('<li>name</li>');
      - prepend
      - before
      - after
    - text()/html(),
      - if given parameter, modify
      - if not, select
    - attr()
      - if give first parameter, select
      - if give second parameter, modify the attribute
    - remove(), remove() the element and its children
    - empty(), empty the children
    - css() chain
      - $('').css('color','yelloe').css('fontSize','20px');
    - animation
      - show()
      - hide()
      - toggle()
    - add/remove class
      - $().addClass('');
      - $().removeClass();
    - find

65. JavaScript ES6 new features

    - Default parameters in function

      - `function(num=1,color='red'){}`

    - Template literals

      - ```javascript
        var url =  `http://localhost:4200/${id}`
        
        ```

    - multi-line string

      - use back-tic `

    - destructuring 

      - ```javascript
        var student = {name:'1',age:1,score:90}
        {name,age} = student;
        
        ```

      - 

    - enhanced object literal

    - arrow function

      - `$().click((event)=>{});`

    - promise

      - ```javascript
        var wait1000 =  new Promise(function(resolve, reject) {
          setTimeout(resolve, 1000)
        }).then(function() {
          console.log('Yay!')
        })
        
        ```

    - block-scoped constructs let and const

      - `for(let i in nums){}`

    - classes 

      - ```javascript
        class MyClass{
            constructor(){
                
            }
        }
        
        ```

    - modules

66. what's AJAX

    - asynchronous javascript and xml
    - update part of the page without reloading the whole page

67. what's dom

    - short for document object model
    - browser load the html file line by line to create a dom tree

68. what's event 

    - event is an object created by browser to represent user interaction
    - contains the information for user interaction(click, scroll up)

69. how to handle an event

    - listen to an event, and register an event handler
    - event handler will automatically invoked

70. event propagation

    - capturing
    - targeting
    - bubbling

71. what's typescript

    - super set of javascript
    - has strong typing
    - need to transpile(transform and compile) ts->js
    - use many java feature, like interface, annotation,enum
    - support 68% of javascript es6



------

### 6. Angular

1. how to create a new angular project
   - ng new project --style=scss
2. how to run the app
   - ng serve
3. what happen during ng serve
   - it'll transpile the typescrpt/scss into javascript/css file
   - it'll package all the files into bundles, uglify and minify them,
   - modify index.html to include those js bundles
   - launch a nodejs (webpack dev server), which is running on 4200 port
4. scss variable
   - $mycolor:white;
5. Module
   - root module (AppModule)
     - will be packaged into 5 js files
   - other modules(lazy loading)
     - each sub-module will generate one js file
6. why we divide the app into modules
   - first screen rendering time is good
7. what's main idea of angular
   - reusable
8. what's component
   - reusable unit contains HTML,CSS,typescript
9. Data binding

- one way 
  - {{}}, double curly braces
- two way data binding
  - import FormsModule
  - use `[(ngModel)]="name"`, name is field name
- attribute binding
  - [], brackets,
- event binding
  - (), parenthesis
  - pass $event to the function

10. what's directive

    - reusable unit as a marker on standard HTML element which bring additional functionalities to the element

11. types of directive

    - attribute directive
      - modify/update DOM element attribute
    - structural directive
      - modify dom tree structure
      - can not have two structural directives on one element

12. component communication

    - parent to child
      - use @Input() in child
      - use attribute binding in parent html to child element
    - child to parent
      - use @Output() in child over EventEmitter
      - create a function to emit the field
      - in parent
        - event binding to that emitter field, 
        - call a functon in the parent, pass $event to it, get the value

13. Service in angular

    - use @Injectable({providedIn:'root'}) to register the service
    - we can use constructor injection to innject the service in other component
    - we can use httpclient in service to send requeset to backend

14. routing

    - angular using routing to implement single page application
    - <router-outlet>as placeholder for specific loading components
    - route configuration
      - path-component mapping
    - RouterLink attribute will request angular to change the path, and prevent reloading

15. pipe

    - used for formatting
    - a reusable function which is used to transform data format for display
    - can only be used in component template(html)
    - like: currency,uppercase, date
    - pipe chaining

16. type of changes

    - pure change
      - primitive value change
      - object/array's reference change
    - impure change
      - object property change
      - array element change

17. types of pipe

    - pure pipe
      - only can detect parameters' pure change and re-run
    - impure pipe
      - can detect pure and impure change and rerun

18. how to define a pipe

    ```typescript
    @Pipe({
        name:'filtere',
        pure:false
    })
    export class FilterPipe implements PipeTransform{
        transform(value:any){
            
        }
    }
    
    ```

19. Observable

    - import from rxjs, which is an independent library
    - it's like a datasource, we can continuously listen to it

20. difference between observable and promise

    - observable
      - .subscribe()
      - preprocess the data
      - no subscribe, no execution, lazy
      - send a stream of data
    - promise
      - .then(), .catch()
      - cannot preprocess
      - it's eager
      - send data once

21. template driven form vs reactive form

    - template driven form
      - easy to setup
      - less configurable
      - difficult to do tests

22. how to handle multiple request at the same time

    - nested requests

      - subscribe
      - mergeMap
      - ![](https://miro.medium.com/max/1400/1*LdHNPjNp_cmsxI4NrSx1Aw.png)

    - parallel requests

      - forkJoin

      ![](https://miro.medium.com/max/1400/1*vdye24UXec5JszhtcTH3YA.png)

23. how to lazy load the third party libarary

    - import the library in the module and lazy load that module
    - https://medium.com/@tomastrajan/why-and-how-to-lazy-load-angular-libraries-a3bf1489fe24

------

 

22. AOT vs JIT. How to configure "ng serve" or "ng build" for AOT? How to build Angular for production?

- Angular compiler: 
  - normally use JIT for development and AOT for production
  - AOT : Ahead Of Time
    - compile views and modules in advance
  - JIT : Just In Time
    - bundle for live-time compiling 
- How to configure for AOT
  - ng serve --aot
  - ng build --aot
- How to build Angular for product
  - ng build --prod

23. Angular data binding. How to do One/Two way , event/attribute binding

    - One way binding
      - double curly braces : {{}}
    - two way binding
      - [(ngModel)]
      - import the FormsModule
    - Event binding
      - parenthesis: ()
      - (onClick)="functionName"
    - attribute binding
      - square bracket: []
      - []

24. How angular implement change detection?

    - Change detection is the way to **synchronize view with model**
    - Angular use **ngZone** (Angular's implementation of zone.js) for change detection.
      - ngZone will **monkey patch** browser's native API.
    - Angular creates **change detector** for each component.
      - When certain actions (browser events, timed events or AJAX requests) happens, ngZone will notify Angular.
    - Angular will run change detectors from root component and update DOM accordingly.
    - Manually trigger change detection
      - OnPush
      - ChangeDetectorRef

25. Exlain life cycle hooks of Angular component/directive

    - Angular offers **lifecycle hooks of component** and directive for developer to **add custom logic**. We can implement certain interface and implement corresponding hook methods.
    - We can use life cycle hooks including
      - `ngOnChange()`
      - `ngOnInit()`
      - `ngDoCheck()`
      - `ngAfterContentInit() `
      - `ngAfterContentChecked`
      - `ngAfterViewInit()`
      - `ngAfterViewChecked()`
      - `ngOnDestroy()`
    - Usage
      - use `ngOnInit()` to call services for initialize data
      - use `ngOnDestroy()` to unsubscribe observables and other variables clean-up

26. Difference between constructor and ngOnInit

    - Constructor function is called **before ngOnInit and even before all life cycle hooks**.
    - ngOnInit is called **after Angular first displays the data-bound properties** and **sets the directive/component's input properties**.

27. Different types of directives in angular. Provide some built in directives

    - attribute directives
      - ngClass
      - ngStyle
    - structural directives
      - ngFor
      - ngIf
      - ngSwtich

28. Explain pipe in angular. How to create custom pipes?

    - Pipe is a **function which transform data from one format to anther in template**
    - I used 
      - CurrencyPipe
      - DecimalPipe
      - UpperCasePipe
    - Custom pipe
      - use **@Pipe decorator** with **pipe metadata** to create a custom pipe.
      - implement **PipeTransform interface's transform method**

    ```typescript
    @Pipe({
        name:'filtere',
        pure:false
    })
    export class FilterPipe implements PipeTransform{
        transform(value:any){
            
        }
    }
    
    ```

29. Pure vs impure pipes

    - Pure pipe can only detect **pure changes**: primitive values and object reference changes
    - Impure pipe can detect pure and **impure changes**: covers object property value and array element changes
    - use **'pure:false'** in pipe metadata to create impure changes. Pure pipe has better performance

30. How to create service in angular

    - use **@Injectable decorator**
    - export the service class

31. How to communicate between components in angular

    - use @Input to pass data from parent to child
    - @Output with event emitters to pass data from child to parent
    - we can also use service for communication

32. What are the core difference between Observables and Promises

    - data 
      - Observable is like **a stream** which **send multiple values over time**
      - Promise only resolve or reject with value once in the future.
    - Cancelable
      - Observable is cancellable(unsubsribe)
      - Promise is not
    - package
      - Observable is from RxJS (Reactive extension javascript libarary)
      - Promise is from JS ES6
    - execute
      - If do not subscribe, Observable won't execute
      - Promise will always execute
    - use `.toPromise()` to convert Observable to Promise

33. What's Subject? Difference between ReplaySubject, BehaviorSubject, AsyncSubject

    - Subject is both observable and observer.
      - send values to Subject by **next()**
      - get value by use **subscribe()**
    - **ReplaySubject** will emits all values to subscriber **regardless of when it subscribes**
    - **BehaviorSubject** emits most recent value to **existing and newly subscriber.**
    - **AsyncSubject** emits last value to subscriber after source complete.
      - it will not emit anything if onCompeleted is not called

34. what's router-outlet

    - router-outlet is a **placeholder** where angular will **dynamically load component based on different routes**

35. what's the difference between forRoot vs forChild

    - use **forRoot** to define routes for root application module
    - use **forChild** for routes in lazy loaded/feature modules

36. How to configure child routes

    - We can define **children property** with **array of child routes** in parent route config object.

37. Have you uses guard service?

    - use guard service to protect and secure angular routes.
    - create VIP section only for VIP users. Non-VIP is not able to access VIP route(URL). We check user's type in the canActivate method of guard service

38. Explain the differences between Template Driven Form vs Reactive Form

    - Form Configuration
      - Template Driven Form requires us to do form configuration with directives in HTML template 
      - Reactive Form requires import of ReactiveFormsModule and creation of FormGroup/FormController instance in component class
    - Implementation
      - Template Driven Form is easy to use and good for simple cases
      - Reactive Form is more powerful and suitable for complex scenarios
    - Testing
      - Reactive form can be unit tested in headless browser

39. How to add from validation to a form built with FormBuilder?

    - use Angular Validators
    - create custom validator for form control or form group

40. what's difference between dirty, touched, pristine on a form element

    - dirty is true if the user **has changed the value** of the control
    - pristine is true if user **hasn't changed the value** of the control
    - touched is true if **the field has been touched** by the user, otherwise it's false

41. How to create custom validator for your form

    - We can create a function as custom validator.
    - The function will **return null if validation passes** otherwise it should **return the error object**
    - we will put the function in the form instance's creation.

42. How to configure different web service API URLs for different environmnets?

    Dev Server API, Test Server API

    - In angular-cli.json file, we can specify configuration file per environment.
    - We can put API URLs as constants in the file and use them in our services.
    - When we run ng build/serve, we can specify an environment option which angular will automatically pick corresponding environment file for current build.

43. What is RouterState and RouterStateSnapshot?

    Have you ever used ActivatedRoute?

    - RouterState represents the state of the router changing over time.
    - RouterStateSnapshot is an immutable data structure representing the state of the router at a particular moment in time.
    - injected the ActivatedRoute as a service to receive route params and check other route information. e.g. url, queryParams
    - [must read](https://vsavkin.com/angular-router-understanding-router-state-7b5b95a12eab)

44. Angular 4 new features

    - Animations module is pulled out of @angular/core as individual BrowserAnimationModule
    - Renderer 2 take place of Renderer
    - *ngIf/else
    - email validation change
    - upgraded to typescript 2.1
    - template changed to ng-template
    - new  title case pipe

45. Angular 5 new features

    - internationalized nubmer, date, and currency pipes
    - exportAs can give different names for components/directives
    - new enhanced HttpClient
    - Angular Forms adds update on Blur/Submit
    - RxJS upgrade to 5.5 e.g. pipe function
    - new Router Lifecycle events

46. what's **switchMap** in rxjs?

    How to convert returned Http response data to observable

    - SwitchMap can be used to convert one observable to another
    - [SwitchMap](https://www.learnrxjs.io/learn-rxjs/operators/transformation/switchmap)

47. List examples of Observables you used in Angular

    - valueChanges, http/httpClient methods, router paramsMap and etc.

48. What is lazy loading module in Angular? How to implement that?

    - We create a **lazy loading module** containing Angular components/services/directives which are **not needed when application launches**
    - we may load the module on the fly when the corresponding routing is triggered.
    - Lazy loading module will help **significantly reduce the build size of main bundle file** which will be loaded when application bootstraps, so as to **improve the first screen rendering time**
    - in routing configuration, we use loadChildren to specify the module we want to load for a route.

49. How did you make your **services available** throughout the **entire angular application**?

    - Before Angular 6, we should put service class in **AppModule's provider array.**
    - After Angular 6, we only need to spcify **@Injectable({providedIn:'root'})** when we create the service

50. Which design pattern is used for designing service in Angular?

    - Dependency Injection. Observable

51. Have you ever used Observable? Have you created cutomized Observable

    - used Observable in Angular Http/HttpClient services to handle AJAX request
    - used of() and interval() methods to create custom observables

52. what are the building blocks have you been exposed to in angular

    - Modules
    - Components
    - Templates
    - Metadata
    - Data binding
    - Directives
    - Services
    - Dependency injection

53. Difference between ngDoCheck and ngOnInit

    - `ngOnChanges()` is called when **a value bound to an input has changed** so you can **run custom code** when an input has changed. It only runs **for pure data changes**.
    - `ngDoCheck()` is called when **change detection runs** so you can **implement your custom change detection action**. It will run for **both pure and impure data changes**

54. Difference between component and directive in angular

    - A component is not the only **UI building block** in Angular. 
    - There are directives which allow you to attach behavior to elements in the DOM
    - Difference
      - a component is **a directive with a view** whereas a **directive is a decorator with no view**
      - Components break up the application into smaller parts
      - Directives add behavior to an existing DOM element

55. What's **tree shaking** in webpack?

    - Tree-shaking is the process of **analyzing your code** and only including the parts you explicitly import your application to run.

56. How to check the changes of fields in angular form?

    - we can get the **FormControl object** and **subscribe the valueChanges observable** to detect latest changes in field.

57. What's interceptor in Angular

    - HttpInterceptor was introduced with Angular 4.3
    - We can create a custom HttpInterceptor to intercept http requests
    - The purpose is add additional headers such as authentication header, content-type and etc. before reqeust is sent.

58. How to optimize in angular application?

    - [Read](https://medium.com/faun/44-quick-tips-to-fine-tune-angular-performance-9f5768f5d945)

59. What is shadow DOM

    - Shadow DOM is introduced in **web component spec** to achieve **style encapsulation**. 
    - Shadow DOM tree is mounted at a shadow root.
    - CSS styles in shadow DOM can't affect outside elements and outside CSS styles will not affect elements in Shadow DOM
    - In angular, we can put component in shadow DOM be setting ViewEncapsulation.ShadowDOM

60. What is host listener for Angular custom directive?

    - we can use @HostListener to bind event listener on host element(who is applied the custom directive)

61. RxJS operators - mergeMap/flatMap vs switchMap vs concatMap

    - All three methods are used when observables(outer) are emitting observables(inner) as data. In this case, you may encounter callback hell if you subscribe each observable. You can chain these methods and subscribe once to gete the final data
    - mergeMap/flatMap 
      - is to map outer observable's data to inner observable and merge the final data into a new output observable. 
      - sequence of data in output observable will not be guaranteed since tit will not wait for previous inner observable to finish
    - switchMap
      - used to map outer observable's data to inner and subscribes internally to get new observable with combined result.
      - but for each new inner observable, it will unsubscribe previous observable even previous one is not completed.
      - used for solving multiple form submission problem
    - concatMap 
      - similar to mergeMap except the data in output observable is **ordered** based on **inner observable sequence** since it will wait for previous inner observable to complete before subscribes to next inner observable

62. What is Transpiling in Angular

    - Transpiling is the process of converting the typescript into javascript.
    - though typescript is used to wirte code in angular appliation, the code is internally transpiled into javascript,
    - since browser can only execute the javascript code

63. What is ngModel in Angular 2+

    - ngModel is a **directive** which can be applied on HTML input, select etc.
    - It's a two-way data binding and it relies on FormsModule.
    - ngModel is represented by [()] so called banana in a box syntax

64. what is an AsyncPipe in angular

    - When an observable or promise return something, we use a temporary property to hold the content. 
    - Later, we bind the same content to the template. 
    - With the usage of AsyncPipe, the promise or observable can be **directly used** in a template and a **temoprary property is not required**

65. Difference between angular and React?

    which one do you recommend to build a frontend  application

    | Angular                   | React                     |
    | ------------------------- | ------------------------- |
    | google product(framework) | Facebook product(library) |
    | component MVC             | only the view of MVC      |
    | user real DOM             | use virtual DOM           |
    | runtime debugging         | compile time debugging    |

66. Have you used tap() operator in rxjs, what does it do?

    - not yet

67. what do feel is the advantage in using ngrx library, is ngrx an angular library

    - not yet

68. how to achieve security in angular

    - not yet

69. why do you use interface in typescript

    - not yet

70. what design pattern do you use in angular?

    - Dependency injection(service)
    - observable
    - decorator
    - component
    - mixin
    - mediator

------

### 7. Maven

1. what's Maven

   - it's a build automation tool 
   - basically, we use it to mange dependencies and build the project

2. how to manage the jar

   - group id
   - artifact id
   - version

3. what's maven's function

   - build package
   - manage dependency

4. how does maven work

   - first will go to .m2 file which is local repository to find the dependency
   - if not, go to central repository to download the package to local

5. what' pom.xml

   - store the dependencies

6. how many maven steps

   there are six steps

   - clean
   - verify
   - compile
   - test
   - package
   - install

7. what' the difference between intall / clean+install

   - cause when we execute install

     if test fail, install won't execute

     but if clean fail, install will still execute

   - clean to ensure clean previous package



### 8. Docker

1. What is docker?

   - Docker is a world's leading **software container platform**

   - it is a tool designed to make it easier to **deploy and run applications by using containers**

   - Containers allow developer to package up an application with all of the environments it needs, such as libraries and other dependencies, and ship it all out as one package

     

2. How docker works

   - create Dockerfile
   - use Dockerfile to `docker build` Docker image
     - directly `docker run` to create instance of docker containers
     - `docker push` to push the image to **Docker Hub** which is the repository of images
   - From **Docker Hub** to `docker pull` the images to the desired environment(server) to `docker run` to create the instance of container
   - Build app only once
     - An application inside a container can run on any system that has docker installed. There is no need to build and configure app multiple times on different platforms

   ![](https://docs.docker.com/engine/images/architecture.svg)

3. Difference between **Virtualization & Containerization**

   - Virtualization
   - Containerization

   ![](https://i.stack.imgur.com/pG94I.png)

4. Explain Docker Architecture

   - Docker has a **client-server** architecture
     - The daemon(server) receives the commands from the Docker client through CLI or REST API
     - Docker client and daemon can be present on the same host(machine) or different hosts

   ![](https://geekflare.com/wp-content/uploads/2019/09/docker-architecture-609x270.png)

5. Advantages of using Docker

   - Build app only once
   - more convenient
     - with docker we can test our application inside a container and ship it inside a container
     - this means the environment in which we test is identical to the one on which the app will run in production
   - Portability
     - Docker containers can run on any platform
   - Version control
     - Like Git, Docker has in-built version control system
     - Docker container work like GIT repository, allowing us to commit changes to the docker images and version control them
   - Isolation
     - With docker every application works in isolation in its own container an does not interfere with other applications running on the same system
     - multiple container can run on same system without interference

6. What are **Docker Images**

   - Docker images are templates used to create Docker containers
   - container is a running instance of image
   - images are store locally or remote(registries e.g. docker hub)
   - docker can build images automatically by reading the instructions from a dockerfile
   - like class and object in java
   - cmd
     - docker images
     - docker pull
     - docker push
     - docker run

7. What are **Docker Containers**

   - Containers are running instances of Docker images
   - Containers isolate software from its surroundings
   - container features
     - lightweight 
     - less resources are used
     - booting of containers is fast
     - can start, stop, kill, remove containers easily and quickly
     - operating system resources can be shared within docker
   - cmd
     - docker p
     - docker run
     - docker start
     - docker pause
     - docker unpause

8. What is **Dockerfile**

   - Dockerfile is a text file with instructions to build image

9. What is **Docker Compose**

   - A tool for defining & running multi-container docker applications

   - use yaml files to configure application services

     - docker-compose.yml

   - can start all service with a single command

     - docker compose up

   - can stop all services with a single command

     - docker compose down

   - can scale up selected services when required

     - --sacle

   - docker compse working

     - install docker compose

     - create docker-compose.yml

     - check validity of file 

       `docker-compose config`

     - run docker-compose.yml file: 

       `docker-compose up -d`

     - bring down application by command

       `docker-compose down`

10. What is **Docker machine**





### 9. Design pattern

- There are three kinds of design pattern in GOF 23
  - Creational design pattern (create objects)
  - Structural design pattern (class and object composition)
  - Behavioral design pattern (communication between objects)

1. GOF

- Creational : create objects
  - Abstract factory
  - Builder (String builder)
  - Factory method (LoggerFactory)
  - Prototype
  - Singleton
- Structural : concern class and object composition
  - Adapter
  - Bridge
  - Composite
  - Decorator (FileInputStream, BufferedInputStream, DataInputStream)
  - Facade (Spring cloud API gateway)
  - Flyweight (string pool)
  - Proxy (Hibernate proxy : placeholder)
- Behavioral : concerned with communication between objects
  - Chain of responsibility (servlet filter)
  - Command
  - Interpreter
  - Iterator
  - Mediator
  - Memento
  - Observer
  - State
  - Strategy
  - Template method
  - Visitor

------

### 10. Gitlab CI/CD





### Terminology

1. what's agile
   - it's a development methodology, which is an approach to project manangement.
   - based on iterative and incremental development, where requirement and solutions evolve through collaboration between teams
   - advantages
     - more flexible
     - more productive
     - more transparent
2. what's OOP
   - Object oriented programming
   - has four main principles
     - Polymorphism
     - Inheritance
     - Encapsulation
     - Abstraction
3. what is multithreading
   - multiple threads exist in one process, which execute independently and simultaneously and share reources
4. what's Garbage collection
   - a mechanism that reclaim heap space from objects which are eligible for garbage collection (normally without reference attached)
5. what's servlet
   - it's a **java program module** that **receives and handles requests** from clients
   - in java only servlet can receive requests
6. what's jsp
   - it's short for java server page, which is used to dynamically generate web pages based on HTML, XML, etc.
7. what's jdbc
   - java database connection
   - it's a java API used to connect the database and execute the query
8. what's JavaMail
   - it's a java API used to send and receive email via SMTP, POP3 these protocol
9. what's RESTful API
   - REST is short for representational state transfer
   - which is an API that uses HTTP requests to GET, POST, PUT, DELETE data
   - advantage compare with SOAP(simple object access protocol) : 
     - less bandwidth
10. what's spring boot
    - a framework to help developer quickly setup and configure the application
    - advantages
      - each application embedded with a tomcat
      - solve the dependency conflicts for use
      - put all the configurations in application.properties file, get rid of all xml configuration files
11. what's spring mvc
    - it's framework which is used to build web application, 
    - it follows model-view-controller design pattern and 
    - implements all the basic features of spring framework like IoC . 
    - It uses dispatcher servlet to handle requests by RequestMapping the url to the controller
12. what's IoC
    - short for Inversion of Control
    - which means developer hand over the control to the object to spring, let spring do the dependency injection for us
13. what's AOP
    - stands for aspect oriented programming
    - it's a programming paradigm that aims to **increase modularity** by allowing the separation of cross-cutting concerns
    - it can add additional behavior to existing code without modification of the code
14. what's spring security
    - it's a customizable access control framework
    - used in our application for security management, including authentication and authorization
15. what's hibernate
    - ORM(object relational mapping) framework for java 
    - which can map the java bean to database table by using annotaion
    - which can also simplify the access to the database
16. what's spring data jpa
    - Spring data jpa is a Java persistence API, which follows JPA specification
    - it handles complex database access and object-relational mapping
    - which also simplify DAO(database access object) layer by providing JpaRepository interface, with which developer can only need to provide abstract method follows jpa naming convention, which will automatically generate sql to access the database
17. what's Spring Integration
    - spring integration is an open source framework for **enterprise application integration**
    - it's a lightweight framework that builds upon the core Spring framework
    - it's designed to enable the development of integration solutions typical of **event-driven architecture and messaging-centric architectures**.
18. what's Microservices
    - also known as microservice architecture 
    - is an architectural style that **structures an application as a collection of services**
    - advantages
      - highly maintainable, testable
      - loosely coupled
      - independently deployable
19. what's Spring cloud
    - Spring cloud is a framework that provides tools for developers quickly build common patterns in distributed system
    - like
      - configuration management
      - service discovery
      - circuit breakers
      - etc
20. What's Ribbon
    - Ribbon is a client-side load balancer that give developer lots of control over the behaviro of HTTP and TCP clients
21. what' Eureka
    - Eureka naming server is an application that holds information about all service applications, also known as discovery server
    - every micro service will register into the eureka naming server
    - eureka naming server knows all the service applications running on which IP address/port
22. what's zuul
    - zuul act as an API Gateway, which sits on top of all other microservices
    - it is built to enable dynamic routing, monitoring, security
23. what's Feign
    - a declarative HTTP client developed by netflix
    - aims at simplifying HTTP API client
    - can be used to send request between microservices
24. what's Hystrix
    - it's a circuit break technique
    - when there's too heavy load, avoid casading failure and provides fallback options
25. what's AJAX
    - asynchronous javascript and xml
    - it's a technique, with which we can send and retrieve data from a server asynchronously and update part of the page without reloading the entire page
26. what's jQuery
    - it's a javascript library which simplify HTML DOM tree manipulation, as well as event handling, and ajax
27. what's bootstrap
    - free, open source css framework
    - directed at responsive, mobile-first frontend web development
    - contains css & javascript based design template for forms, buttons, etc.
28. what's RxJS
    - short for **Reactive extension for javascript**
    - libarary for reactive programming using observables that make it easier to compose asynchronous or callback-based code
29. What's relational database
    - relational database is a collection of relations of two dimensional tables
30. what's sequence
    - sequence is a sharable object that automatically generates unique numbers
    - normally used to create  primary key value
31. what's trigger
    - trigger is a specical stored procedure, which cannot be called directly
    - it is implicitly invoked when an insert, update, delete is issued against the associate table
32. what's junit
    - JUnit is an open source Unit testing framework for java
    - it's important in the development of test-driven development
33. what's mockito
    - open source testing framework for java
    - allows creation of test double objects(mock objects) in automated unit tests
34. what's Log4j
    - log4j is a open source logging framework
    - with log4j - logging behavior can be controlled by editing a configuration file 
    - it equips the user with detailed context for application failures
35. what's Jasmine
    - open source unit testing framework for javascript
    - it aims to run on any javascript-enabled platform
36. what's Karma
    - Karma is a task runner for our test
    - Using karma to run testes using one javascript testing tool like jasmine
37. what's E2E, Protractor
    - e2e stands for end to end or UI testing
    - is a methodology used to test whether the flow of an application is performing as designed from start to end, it's a blackbox testing tool
    - Protractor
      - is an end to end test framework for angular and angularjs application
      - protractor can work with selenium to provide an automated test infrastructure that can simulate user's interaction with angular application running in a browser.
      - https://www.protractortest.org/#/infrastructure
38. what's AWS, EC2, S3, RDS, Elastic Bean stalk
    - AWS : Amazon web service 
      - a platform providing cloud computing services
    - EC2
      - Elastic Compute Cloud, 
    - S3
      - Simple Storage Service
    - RDS
      - Relational Database service
    - Elastic Bean stalk
39. why people use RDS
    - it's easy to setup, operate and scale
    - also it provide security group to avoid unwanted access
40. What's TypeScript
    - TypeScript is a super set of javascript
    - which provides strong typing
    - need to transpile (transform + compile) ts-> js
    - use many java like feature :interface, annotation,enum
    - support 68% of javascript ES6 features
41. what' JMS
    - short for Java Message service API 
    - is a java message-oriented middleware API for sending message between clients
    - it's an implementation to handle the producer-consumer pattern
42. what's Angular material
    - UI component libarary for Angular which follows material design
    - help in constructing attractive, functional web pages and applications
    - material design is a design language developed by google
43. what's Tomcat
    - Tomcat is a web server which is designed to execute java servlets and render web pages
    - 
44. what's maven
    - it's a **build automation tool **
    - basically, we use it to **mange dependencies and build the project**
45. what's JIRA
    - **issue tracking product**
    - commonly used for bug tracking, issue tracking, and project management
46. what's GIT/SVN
    - GIT 
      - a distributed **version-control system** for **tracking changes** in source code during software development
    - SVN
      - short for Apache Subversion
      - software versioning and revision control system.





### Summary

1. HTML 5

   - header, footer
   - svg, canvas
   - audio, video

2. css 3

   - rounded corner
   - box shadow
   - text shadow
   - gradient
   - RGBA, color with opacity
   - Transform

3. Angular lifecycle hook methods

   - ngOnInit
   - ngOnChanges
   - ngOnDestroy
   - ngDoCheck
   - ngAfterContentInit
   - ngAfterContentChecked
   - ngAfterViewInit
   - ngAfterViewChecked

4. GOF

   - Creational : create objects
     - Abstract factory
     - Builder (String builder)
     - Factory method (LoggerFactory)
     - Prototype
     - Singleton
   - Structural : concern class and object composition
     - Adapter
     - Bridge
     - Composite
     - Decorator (FileInputStream, )
     - Facade (Spring cloud API gateway)
     - Flyweight (string pool)
     - Proxy (Hibernate proxy : placeholder)
   - Behavioral : concerned with communication between objects
     - Chain of responsibility (servlet filter)
     - Command
     - Interpreter
     - Iterator
     - Mediator
     - Memento
     - Observer
     - State
     - Strategy
     - Template method
     - Visitor

5. adapter design pattern

   - allows the interface of an existing class to be used as another interface.

6. jdbc

   - java database connection
   - Statement, PreparedStatement, CallableStatement

7. Angular JS

   - an open source Model-View-Controller javascript framework to build single page application
   - main features
     - MVC
     - Data model binding

8. Angular

   - typeScript-based web application framework

9. what's Spring Integration

   - spring integration is an open source framework for **enterprise application integration**
   - it's a lightweight framework that builds upon the core Spring framework
   - it's designed to develop integration solutions typical of **event-driven architecture and messaging-centric architectures**.

10. what's E2E, Protractor

    - e2e stands for end to end or UI testing
    - is a methodology used to test whether the flow of an application is performing as designed from start to end,
      - it's a blackbox testing tool
    - Protractor
      - is an end to end test framework for angular and angularjs application
      - protractor can work with selenium to provide an automated test infrastructure that can simulate user's interaction with angular application running in a browser.
      - https://www.protractortest.org/#/infrastructure

11. Strict mode in javascript

    - Javascript strict mode is for writing more secure code.
    - we can enable strict mode for global or for function by 'use strict'; statement
    - Under strict mode, we can avoid accidentally creating global variables.
    - Also, certain actions will throw an error. 
      - assign value to non-extensible property
      - delete a variable
      - duplicate parameter name

    

12. Angular 8 new features

    - preview of Ivy
    - differential loading
    - dynamic imports for lazy-loaded routes
    - CLI workflow improvements

13. Angular 4 new features

    - ng-template
    - animation package

14. Difference between angular and angular js

    - one use typescript, another use javascript
    - angular js is mvc framework, angular is based on component structure
    - template name change, ng-repeat, ngFor

15. why migrate from angular js to angular

    - javascript is weak typing ,cause type error
    - angular js is less reusable

16. Stream API

    - Stream API provides functional approach to processing collections of objects
    - Non-terminal operations
      - filter
      - map
        - 
      - flatMap
        - if nested, move nested object out
      - distinct
        - remove duplicates
      - limit
        - limit the elements number
      - peek
        - return a new stream with all the elements
    - terminal operations
      - collect
      - forEach
      - reduce
      - min/max
      - count
      - anyMatch
      - allMatch
      - nonMatch
      - findAny
      - findFirst

17. workflow of spring mvc

    - A request goes through      DispatcherServlet,
    - use @Controller to find a      controller class
    - use @RequestMapping to find      the corresponding emthod to handle the request
    - then the method returns a      ModelAndView object to DispatcherServlet, in which model contains data and      view contains a string that will be converted to a real url by      ViewResolver
    - DispatcherServlet send the      view object to the ViewResolver to get the actual view page
    - Finally dispatcherServlet      will pass the Model object to the view page to display the result and      fulfil the reponse body and send it back

18. Transaction

    - DML statements that make up one consistent change to the data
    - end with commit or rollback

19. temporary table

    - global temporary table 
      - is temporary
      - visible to all sessions with appropriate privilidges
    - data in temporary table is visible only to the session that insert the data into the table

20. View

    - logically represents subsets of data from one or more table

21. Sequence

    - a sharable object that automatically generates unique numbers

22. index

    - designed to increase performance of a query

23. stored procedure

    - a sequence of operations available to applications that access a RDBMS

24. difference between stored procedure and function

    - function has unique return type
    - stored procedure doesn't have a return value, but input can work as output

25. trigger

    - special stored procedure, implicitly invoked when insert, update, delete statement is issued against associated table
