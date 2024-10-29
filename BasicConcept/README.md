# Java Concept
### Key Features of Java
- **Object-Oriented**: Everything in Java is an object, which helps with modularity and reuse.
- **Platform-Independent**: Thanks to the JVM, Java code can run on any platform. The Java Virtual Machine (JVM) is a virtual machine that allows Java programs to run on various operating systems and platforms. It acts as an interpreter between the Java programming language and the underlying hardware.
- **Robust**: Java has strong memory management, exception handling, and garbage collection.

### Memory Management
- **Stack Memory**: Stores primitive data types and object references. It is organized in a Last In, First Out (LIFO) manner and is limited in size, making it quick for allocation and deallocation.
- **Heap Memory**: Where all objects are stored. The heap is shared among all threads, allowing for dynamic memory allocation, managed by automatic garbage collection to prevent memory leaks.

### Error Handling Structure
- **try-catch**: Code that may throw an exception is wrapped in a `try` block, with one or more `catch` blocks to handle specific exception types.
- **finally**: This block executes after the `try-catch` blocks, regardless of whether an exception was thrown. It is often used to release resources.
- **throw/throws**: `throw` is used to explicitly throw an exception, and `throws` in a method signature indicates the method may throw a particular exception.

### Garbage Collection in Java
Garbage Collection (GC) in Java is an automated process that reclaims memory by removing objects that are no longer in use, preventing memory leaks. The JVM has multiple garbage collection algorithms, each suited to different application needs, such as throughput or low-latency requirements. Key algorithms include:
- **Serial GC**: Processes garbage collection in a single thread, suitable for single-threaded applications.
- **Parallel GC**: Also known as the throughput collector, it uses multiple threads for garbage collection, improving performance for multi-threaded applications.

### Multithreading
Java supports concurrent execution, enabling better performance by allowing multiple threads to run in parallel.

### Security
Java has built-in security features, including a bytecode verifier and security manager.

## Java Collections Framework
Java Collections Framework includes various data structures:
- **List**: e.g., `ArrayList`, `LinkedList`, which allow duplicates and maintain insertion order.
- **Set**: e.g., `HashSet`, `TreeSet`, which do not allow duplicates and do not guarantee order.
- **Map**: e.g., `HashMap`, `TreeMap`, which store key-value pairs and do not allow duplicate keys.
- **Queue**: e.g., `PriorityQueue`, which is used for processing elements in a particular order.

### Difference between Set and List
- **Set**: Does not allow duplicate elements, is typically unordered.
- **List**: Allows duplicates and maintains insertion order.
- **Implementation**: `HashSet` is implemented using a hash table, whereas `ArrayList` is backed by a dynamic array.

### List and Set Implementations
- **List**: `ArrayList`, `LinkedList`, `Vector`
- **Set**: `HashSet`, `TreeSet`, `LinkedHashSet`

## Core Java Concepts
- **Override**: Modifying a method in a subclass that’s defined in the superclass.
- Overriding is used when a subclass needs to change the behavior of a method that it inherits from the superclass.
- This allows the subclass to provide a specific implementation of a method that is already defined in its parent class.
- Here, the Dog class overrides the sound() method from the Animal class. Even though myDog is of type Animal, it calls the overridden sound() method in Dog.
```JAVA
class Animal {
    public void sound() {
        System.out.println("This is an animal sound");
    }
}

class Dog extends Animal {
    // Overriding the sound() method in the superclass
    @Override
    public void sound() {
        System.out.println("Woof Woof");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        myDog.sound();  // Output: Woof Woof
    }
}
```
- **Overload**: Defining multiple methods in the same class with the same name but different parameters.
- Overloading allows a class to define multiple methods with the same name but different parameters. This enables the method to handle different types or numbers of inputs.
- Here, the add method is overloaded with different parameter lists, so it can add either two or three integers or two doubles.
```JAVA
class MathOperations {
    // Overloaded method for two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Overloaded method for three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Overloaded method for two doubles
    public double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        MathOperations math = new MathOperations();
        System.out.println(math.add(10, 20));          // Output: 30
        System.out.println(math.add(10, 20, 30));      // Output: 60
        System.out.println(math.add(10.5, 20.5));      // Output: 31.0
    }
}
```
- **Inheritance**: Allows a class to inherit properties and methods from another class.
- Inheritance allows one class to inherit fields and methods from another class, promoting reusability and modularity.
- The subclass, or child class, extends the superclass, or parent class, gaining its attributes and behaviors.
- Here, Car inherits the start() method from Vehicle and adds its own honk() method. This demonstrates how Car reuses and extends the behavior of Vehicle.
```JAVA
class Vehicle {
    public void start() {
        System.out.println("Vehicle is starting");
    }
}

class Car extends Vehicle {
    public void honk() {
        System.out.println("Car is honking");
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.start();  // Output: Vehicle is starting
        myCar.honk();   // Output: Car is honking
    }
}
```
- **final Keyword**: Used to prevent inheritance, prevent method overriding, or define constants.
- The final keyword can serve different purposes depending on where it’s used:
- **Final Variable**: When a variable is declared as final, its value cannot be changed after it’s initialized.
- **Final Method**: A final method cannot be overridden by subclasses.
- **Final Class**: A final class cannot be subclassed.
- In this example:
- The PI constant in Constants class cannot be modified.
- The sleep() method in Animal is final and can’t be overridden in Bird.
- The Fish class is final, so it cannot have subclasses.
- These examples demonstrate how overriding, overloading, inheritance, and the final keyword can be strategically used to design robust and flexible code structures.
```JAVA
class Constants {
    public static final double PI = 3.14159;
}

class Animal {
    public final void sleep() {
        System.out.println("Animal is sleeping");
    }
}

final class Fish {
    public void swim() {
        System.out.println("Fish is swimming");
    }
}

class Bird extends Animal {
    // Trying to override sleep() would cause a compilation error
    // public void sleep() { ... } // Error: cannot override final method
}

public class Main {
    public static void main(String[] args) {
        System.out.println("Value of PI: " + Constants.PI); // Output: 3.14159

        Fish fish = new Fish();
        fish.swim();  // Output: Fish is swimming

        Bird bird = new Bird();
        bird.sleep();  // Output: Animal is sleeping
    }
}
```

## HTTP and RESTful APIs
- **HTTP Methods**:
  - **GET**: Retrieves data from a server.
  - **POST**: Sends data to the server, often used for creating resources.
  - **Other methods** include `PUT` (update), `DELETE` (delete), `PATCH`, etc.
- **RESTful APIs**: RESTful APIs are an architectural style for creating web services. They use HTTP methods and follow specific principles, like statelessness and resource-based URIs, to enable standardized and scalable web communication.

- **Statelessness**: Each client request must contain all necessary information since the server does not store session data between requests. This enables easier scaling and reliability, allowing any server in a cluster to handle any request independently.

- **Resource-Based URIs**: Each resource (e.g., users, orders) has a unique URI, making the API intuitive and organized. For example:
  - **GET /users/123**: Retrieves user with ID 123.
  - **POST /users**: Creates a new user.
  
