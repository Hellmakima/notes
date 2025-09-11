# Object-Oriented Programming (OOP)

#### **1. Class**
A blueprint for creating objects, defining attributes (data) and methods (functions) to manipulate the data.

#### **2. Object**
An instance of a class, representing a specific example with actual attribute values.

#### **3. Encapsulation**
Bundling data and methods into a class, restricting direct access to data to prevent misuse and ensure data integrity.

#### **4. Inheritance**
A mechanism allowing one class (subclass) to inherit attributes and methods from another (superclass), promoting code reuse and hierarchy.

#### **5. Polymorphism**
Allows objects of different classes to be treated as objects of a common superclass. The method executed is determined at runtime via **method overriding** or **overloading**.

#### **6. Abstraction**
Hides complex details and shows only essential features, simplifying interaction with complex systems.

---

### **Additional Concepts**

#### **1. Advantages of OOP Over Functional Programming**
- **Functional programming is writing code using functions that don’t change things. You give them inputs, they give you outputs. No changing values, just pure math-like logic.**
- **Reusability**: Inheritance promotes reusability of code.
- **Maintainability**: Encapsulation hides complexity, making the code easier to maintain.
- **Scalability**: OOP systems are easier to scale due to modularity and organization.

#### **2. Key Concepts**   

- **Constructor and Destructor**:  
   - **Constructor**: Initializes objects when created.
   - **Destructor**: Cleans up when an object is destroyed.
  
- **Types of Inheritance**:
   1. **Single Inheritance**: One class inherits from a single class.
   2. **Multiple Inheritance**: A class inherits from multiple classes.
   3. **Multilevel Inheritance**: A class inherits from another derived class.
   4. **Hierarchical Inheritance**: Multiple classes inherit from a single base class.

- **Types of Polymorphism**:
   1. **Compile-time (Static) Polymorphism**: Achieved through **method overloading**.
   2. **Runtime (Dynamic) Polymorphism**: Achieved through **method overriding**.

- **Abstract Classes and Methods**:  
   - **Abstract Class**: A class that cannot be instantiated, meant to be subclassed.
   - **Abstract Method**: A method that has no implementation in the base class and must be implemented by subclasses.

- **Virtual, Default, and Abstract Functions**:
   - **Virtual Function**: A method in the base class that can be overridden in derived classes.
   - **Default Function**: A method with a default implementation in the base class.
   - **Abstract Function**: A method with no implementation in the base class, forcing subclasses to implement it.

- **What Can and Can’t Be Overridden**:
   - **Overridden**: Methods in base classes can be overridden in derived classes (virtual methods).
   - **Cannot Be Overridden**: Static methods, constructors, and destructors.

---

### **Design Principles**

- **SOLID**: A set of principles for designing maintainable, flexible, and scalable software:
  1. **S**: Single Responsibility Principle (SRP)
  2. **O**: Open/Closed Principle (OCP)
  3. **L**: Liskov Substitution Principle (LSP)
  4. **I**: Interface Segregation Principle (ISP)
  5. **D**: Dependency Inversion Principle (DIP)

- **DRY (Don’t Repeat Yourself)**: A principle aimed at reducing duplication of code by promoting reusability.

- **KISS (Keep It Simple, Stupid)**: Encourages simplicity in design, avoiding unnecessary complexity.

