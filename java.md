# Java

### **Java Development and Runtime Environment**

```
 ______________________________________
 |              JDK                   |
 |  _________  _____________________  |
 |  |DEV    |  |        JRE        |  |
 |  |TOOLS  |  |   _____   _____   |  |
 |  |_______|  |   |JVM|   |LIB|   |  |
 |             |   |___|   |___|   |  |
 |             |___________________|  |
 |____________________________________|
```

1. **JDK (Java Development Kit)**
   - **Purpose**: A set of development tools for creating Java applications, including the Java compiler (`javac`), debugger, and libraries.
   - **Components**:
     - **DEV TOOLS**: Tools used by developers for compiling and debugging Java code.
     - **JRE**: Java Runtime Environment, includes JVM and core libraries.
2. **JRE (Java Runtime Environment)**

   - **Purpose**: Provides the necessary environment to run Java applications. It includes the JVM (Java Virtual Machine) and core libraries.
   - **Components**:
     - **JVM**: Executes bytecode and manages memory, garbage collection, and platform independence.
     - **LIB (Libraries)**: Core libraries and APIs required to run Java programs.

3. **JVM (Java Virtual Machine)**

   - **Function**: Executes compiled bytecode and provides memory management and garbage collection.
   - **Key Features**:
     - Bytecode execution
     - Platform independence

4. **JIT (Just-In-Time Compiler)**
   - **Function**: Converts bytecode into native machine code at runtime, improving performance.

---

### **Memory for a Program**

| Segment                      | Description                              | Growth Direction |
| ---------------------------- | ---------------------------------------- | ---------------- |
| **Stack**                    | Stores method frames and local variables | Downward         |
| **Heap**                     | Stores dynamically allocated memory      | Upward           |
| **BSS (Uninitialized Data)** | Stores uninitialized variables           | -                |
| **Data (Initialized Data)**  | Stores initialized variables             | -                |
| **Text (Code)**              | Stores executable code (fixed size)      | -                |

```
+------------------------------+
|    Stack                     |  <-- Growing downward
+------------------------------+
|    Heap                      |  <-- Growing upward
+------------------------------+
|    BSS (Uninitialized Data)  |
+------------------------------+
|    Data (Initialized Data)   |
+------------------------------+
|    Text (Code)               |  <-- Fixed size
+------------------------------+
```

---

### **Java Methods and Overriding**

1. **Methods That Can't Be Overridden**:
   - **Static Methods**: Cannot be overridden, only hidden.
   - **Final Methods**: Cannot be overridden.
   - **Private Methods**: Not visible to subclasses.
   - **Abstract Methods**: Must be overridden by subclasses or the class must be abstract.
   - **Constructor Methods**: Cannot be overridden.
   - **Interface Methods**: Implemented, not overridden.

---

### **Java Utility Classes**

1. **Arrays**

   - **Common Methods**:
     - `Arrays.fill(a, -2)`
     - `Arrays.sort(a)`
     - `Arrays.copyOf(a, newLength)`
     - `Arrays.equals(a1, a2)`
     - `Arrays.toString(a)`

2. **List**

   - **Common Methods**:
     - `add(T element)`
     - `get(int index)`
     - `remove(int index)`
     - `size()`
     - `contains(Object element)`
     - `set(int index, T element)`

3. **ArrayList**

   - **Common Methods**:
     - `add(T element)`
     - `get(int index)`
     - `remove(int index)`
     - `size()`
     - `contains(Object element)`
     - `subList(from, to)`
     - `clear()`

4. **HashMap**

   - **Common Methods**:
     - `put(K key, V value)`
     - `get(Object key)`
     - `remove(Object key)`
     - `containsKey(Object key)`
     - `containsValue(Object value)`
     - `size()`

5. **Queue**

   - **Common Methods**:
     - `add(T element)`
     - `poll()/remove()`
     - `peek()`

6. **PriorityQueue**
   - **Common Methods**:
     - `add(T element)`
     - `poll()/remove()`
     - `isEmpty()`
     - `peek()`

---

### **Java Key Concepts**

1. **Key Features of Java**:

   - Platform independence via bytecode and JVM.
   - Robust memory management with garbage collection.
   - Object-oriented programming model with inheritance, polymorphism, and encapsulation.

2. **Interfaces**:

   - **Definition**: A contract that classes must adhere to.
   - **Details**: An interface can declare methods without providing implementations. Classes implement these methods.

3. **Packages**:

   - **Purpose**: Organizes classes and interfaces to avoid naming conflicts and to provide better access control.
   - **Common Packages**: `java.util`, `java.io`, `java.lang`.

4. **Collections Framework**:

   - A set of classes and interfaces that implement commonly reusable collection data structures.
   - Includes classes like `ArrayList`, `HashMap`, `LinkedList`, and `HashSet`.

5. **Garbage Collection**:

   - **Purpose**: Automatic memory management to reclaim unused memory.
   - **Mechanisms**: Mark-and-sweep, reference counting, and generational garbage collection.

6. **Final vs. Finally vs. Finalize**:

   - **final**: Used to define constants, prevent method overriding, and prevent class inheritance.
   - **finally**: Block that executes after try-catch for cleanup operations.
   - **finalize**: Method invoked by garbage collector before an object is destroyed.

7. **Streams**:

   - **Definition**: A sequence of data elements that can be processed in a functional style.
   - **Types**: Input and output streams (`InputStream`, `OutputStream`), with specific implementations like `FileInputStream`, `FileOutputStream`.

8. **>> and >>> Operators**:

   - **>>**: Signed right shift operator (preserves sign bit).
   - **>>>**: Unsigned right shift operator (fills with 0 regardless of sign).

9. **JDBC (Java Database Connectivity)**:

   - **Purpose**: A set of Java APIs to connect to databases and execute SQL queries.
   - **Use**: Allows interaction with relational databases through SQL.

10. **Multithreading and Synchronization**:

    - **Multithreading**: Running multiple threads in parallel to achieve concurrent execution.
    - **Synchronization**: Prevents thread interference by ensuring that only one thread can access a resource at a time.

11. **Executor Framework**:

    - Provides high-level APIs for managing and controlling thread execution (e.g., `ExecutorService`, `ThreadPoolExecutor`).

12. **Reflection API**:

    - Allows Java code to inspect and manipulate classes, methods, and fields at runtime.

13. **Threads and Its Syntax**:

    - **Thread Creation**: Using `Thread` class or `Runnable` interface.
    - **Syntax**:
      ```java
      Thread t = new Thread(new Runnable() {
          public void run() {
              // code
          }
      });
      t.start();
      ```

14. **Pipes**:

    - Provides a mechanism for inter-thread communication and data transfer through byte or character streams.

15. **Templates**:

    - **Definition**: Used in Java generics to define methods and classes with a placeholder for object types.

16. **Errors, Exceptions, and Types**

17. **Errors**

    - **Definition**: Critical issues that occur in the application, often related to system-level failures, which cannot be handled programmatically.
    - **Common Types of Errors**:
      - **StackOverflowError**: Thrown when the stack memory overflows, often due to infinite recursion.
      - **OutOfMemoryError**: Thrown when the JVM runs out of memory for new objects.

18. **Exceptions**

    - **Definition**: Events that disrupt the normal flow of a program, which can be handled programmatically using try-catch blocks.
    - **Types of Exceptions**
    - **Checked Exceptions**:
      - Exceptions that must be handled (caught or declared in the method signature) during compile-time.
      - Examples:
        - `IOException`
        - `SQLException`
        - `FileNotFoundException`
    - **Unchecked Exceptions**:
      - Exceptions that occur at runtime and are not required to be declared or caught.
      - Examples:
        - `NullPointerException`
        - `ArrayIndexOutOfBoundsException`
        - `ArithmeticException`

19. **Interfaces**:

```java
// Defining an interface
interface MyInterface {
 // Abstract method
 void method1();

 // Default method
 default void method2() {
     System.out.println("Default implementation of method2");
 }

 // Static method
 static void method3() {
     System.out.println("Static method in interface");
 }
}

class a implements MyInterface {
 @Override
 public void method1() {
     System.out.println("Implemented method1");
 }

 public static void main(String[] args) {
     a obj = new a();
     obj.method1();         // Calls the implemented method
     obj.method2();         // Calls the default method
     MyInterface.method3(); // Calls the static method
 }
}

```

In Java, an **interface** is a reference type that defines a set of abstract methods (methods without a body) that a class can implement. An interface is used to achieve **abstraction** and **multiple inheritance** in Java.

### Key Features of Java Interfaces

1.  **Abstract Methods**: All methods in an interface are abstract by default (prior to Java 8). These methods must be implemented by the class that implements the interface.
2.  **Constants**: All fields in an interface are `public`, `static`, and `final` by default.
3.  **Default Methods**: Introduced in Java 8, allows interfaces to have methods with a default implementation.
4.  **Static Methods**: Interfaces can have static methods since Java 8.
5.  **Private Methods**: Since Java 9, interfaces can have private methods to support reusable code within the interface.

### Why Use Interfaces?

1.  **Multiple Inheritance**: A class can implement multiple interfaces.
2.  **Polymorphism**: Interfaces allow objects to be treated as instances of their interface types.
3.  **Design Contracts**: Interfaces define a contract for classes, ensuring consistency across implementations.
