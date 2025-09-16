# Coding

---

## **Programming Concepts**

### **Asymptotic Notations**

Asymptotic notations describe the efficiency of an algorithm as the input size grows. They help in analyzing time and space complexities.

- **Big-O Notation (O)**: Upper bound; describes the worst-case scenario.

  - Example: Binary search \( O(\log n) \).

- **Omega Notation (Ω)**: Lower bound; describes the best-case scenario.

  - Example: Searching in a sorted array \( Ω(1) \).

- **Theta Notation (Θ)**: Tight bound; when the upper and lower bounds are the same.
  - Example: Linear search \( Θ(n) \).

#### **Visualization of Growth Rates**

Common complexity classes (with examples):

- \( O(1) \): Array indexing (constant time).
- \( O(\log n) \): Binary search.
- \( O(n) \): Linear search.
- \( O(n \log n) \): Merge sort, Quick sort (average case).
- \( O(n^2) \): Nested loops.
- \( O(2^n) \): Recursive Fibonacci.

**Graph Example**: Depict these complexities on a graph to show their relative growth.

---

### **Scope: Global and Local Variables**

- **Global Variables**:

  - Declared outside any function or method.
  - Accessible across the entire program.
  - Risk of unintended side effects if overused.

- **Local Variables**:
  - Declared within a function, block, or method.
  - Accessible only within that specific scope.

#### **How to Access and Use Scope in Java**

1. **Global Scope**:  
   Variables defined at the class level and marked `static` behave as global variables.

   ```java
   public class ScopeExample {
       static int globalVar = 10; // Global variable

       public static void main(String[] args) {
           System.out.println("Global Variable: " + globalVar);
       }
   }
   ```

2. **Local Scope**:  
   Variables declared inside methods or blocks:

   ```java
   public class ScopeExample {
       public static void main(String[] args) {
           int localVar = 20; // Local variable
           System.out.println("Local Variable: " + localVar);
       }
   }
   ```

3. **Access Modifiers**:  
   `public`, `private`, `protected`, and default control variable visibility across scopes.

---

### **Errors and Exceptions**

#### **Definitions**

1. **Errors**: Unrecoverable problems usually due to resource limitations.

   - Examples: `StackOverflowError`, `OutOfMemoryError`.

2. **Exceptions**: Recoverable issues that can be handled.
   - **Checked Exceptions**:
     - Must be explicitly declared or handled.
     - Example: `IOException`, `SQLException`, `FileNotFoundException`.
   - **Unchecked Exceptions**:
     - Do not need explicit handling.
     - Example: `NullPointerException`, `ArithmeticException`, `ArrayIndexOutOfBoundsException`.

#### **Handling Exceptions: try-catch-finally**

```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            int divideByZero = 5 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Caught Exception: " + e.getMessage());
        } finally {
            System.out.println("Finally block always executes.");
        }
    }
}
```

#### **Creating Custom Exceptions**

```java
class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}
```

#### **Best Practices**

- Catch specific exceptions before general ones.
- Avoid empty `catch` blocks.
- Use `finally` for resource cleanup.

---

### **Deep vs. Shallow Copy**

1. **Shallow Copy**:

   - Copies only the top-level structure.
   - Sub-objects or references still point to the same memory.

   ```java
   class ShallowExample {
       int[] data = {1, 2, 3};
   }

   ShallowExample shallowCopy = original; // Changes to `data` affect both.
   ```

2. **Deep Copy**:

   - Creates an independent copy of the object and all its nested sub-objects.

   ```java
   class DeepExample implements Cloneable {
       int[] data = {1, 2, 3};

       public DeepExample clone() {
           DeepExample copy = new DeepExample();
           copy.data = data.clone(); // Independent data array
           return copy;
       }
   }
   ```

#### **Use Cases**

- **Shallow Copy**: Efficient for immutable or non-nested data structures.
- **Deep Copy**: Required for independent manipulation of deeply nested objects (e.g., cloning configurations).

---

### **Lambda Functions in Java**

Introduced in Java 8, lambda functions provide a concise syntax for functional programming.

Commonly used for stream operations, such as `map`, `filter`, and `reduce`, processing large datasets with Streams for parallelism.

#### **Syntax**

```java
(parameter_list) -> { body }
```

#### **Example**

```java
Consumer<String> greet = name -> {
    System.out.println("Hello, " + name);
};
greet.accept("Alice"); // Output: Hello, Alice
```

#### **Common Uses**

- **Streams API**: Functional operations such as `map`, `filter`, and `reduce`.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
List<Integer> squares = numbers.stream()
                                .map(x -> x * x)
                                .collect(Collectors.toList());
System.out.println(squares); // Output: [1, 4, 9, 16]
```

- **Threading**:

```java
new Thread(() -> System.out.println("Thread running")).start();
```

#### **Method References**

A concise way to express lambdas using `::`.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(System.out::println);
```
