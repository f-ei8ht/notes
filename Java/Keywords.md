# Java Keywords Complete Reference

All 50 Java keywords with detailed usage explanations:

### **1. `abstract`**

The `abstract` keyword is used to declare a class or method as abstract.

- Abstract classes cannot be instantiated.
- Abstract methods are declared without an implementation.

---

### **2. `assert`**

The `assert` keyword describes a predicate (a true/false statement) placed in the code to ensure a condition holds true.

- If the assertion evaluates to `false`, an assertion failure occurs, typically aborting execution.
- Optionally enabled by the ClassLoader method.

---

### **3. `boolean`**

The `boolean` keyword defines a variable that holds either `true` or `false`.

- Default value: `false`.
- Also used to declare a method returning a `boolean` value.

---

### **4. `break`**

The `break` keyword is used to:

1. Exit prematurely from a `for`, `while`, or `do-while` loop.
2. Mark the end of a `case` block in a `switch` statement.

---

### **5. `byte`**

The `byte` keyword declares an 8-bit signed two's complement integer variable.

- Range: -128 to 127.
- Also used to declare that a method returns a `byte` value.

---

### **6. `case`**

The `case` keyword labels statements in a `switch` block.

- The `switch` expression evaluates and matches a `case` label.
- Statements following the matching `case` are executed until a `break` is encountered.

---

### **7. `catch`**

The `catch` keyword is used with `try` and optionally `finally` blocks to handle exceptions.

- Specifies what to do if a specific type of exception is thrown by the `try` block.

---

### **8. `char`**

The `char` keyword declares a variable to store a single 16-bit Unicode character.

- Range: '\u0000' (0) to '\uffff' (65,535 inclusive).
- Wrapper class: `Character`.

---

### **9. `class`**

The `class` keyword defines a class in Java.

- A class is a blueprint for creating objects.
- It encapsulates common properties and behaviors of objects.

---

### **10. `continue`**

The `continue` keyword skips the current iteration of a loop and resumes execution at the next iteration.

- Unlabeled `continue`: Skips to the end of the innermost loop.
- Labeled `continue`: Skips to the end of the specified enclosing loop.

---

### **11. `const`**

The `const` keyword is reserved but not used in Java.

- Originally intended for declaring constants.
- Use `final` instead for constant declarations.

---

### **12. `default`**

The `default` keyword has multiple uses:

1. In `switch` statements: Specifies the default case when no other case matches.
2. In interfaces: Defines default method implementations (Java 8+).
3. In annotations: Specifies default values for annotation elements.

---

### **13. `do`**

The `do` keyword starts a `do-while` loop.

- The loop body executes at least once before the condition is checked.
- Syntax: `do { statements } while (condition);`

---

### **14. `double`**

The `double` keyword declares a 64-bit floating-point variable.

- Range: approximately ±1.7e±308 (15 decimal digits).
- Default value: 0.0d.
- Wrapper class: `Double`.

---

### **15. `else`**

The `else` keyword provides an alternative execution path in conditional statements.

- Used with `if` statements to execute code when the condition is false.
- Can be chained with `else if` for multiple conditions.

---

### **16. `enum`**

The `enum` keyword defines an enumeration type (added in Java 5.0).

- Creates a special class that represents a group of constants.
- Enums can have constructors, methods, and instance variables.

---

### **17. `extends`**

The `extends` keyword establishes inheritance between classes.

- A subclass extends a superclass to inherit its properties and methods.
- Java supports single inheritance only (one class can extend only one other class).

---

### **18. `final`**

The `final` keyword prevents modification:

1. Variables: Creates constants that cannot be reassigned.
2. Methods: Prevents method overriding in subclasses.
3. Classes: Prevents class inheritance.

---

### **19. `finally`**

The `finally` keyword defines a block that always executes after a `try-catch` block.

- Executes regardless of whether an exception was thrown or caught.
- Commonly used for cleanup operations like closing resources.

---

### **20. `float`**

The `float` keyword declares a 32-bit floating-point variable.

- Range: approximately ±3.4e±38 (6-7 decimal digits).
- Default value: 0.0f.
- Wrapper class: `Float`.

---

### **21. `for`**

The `for` keyword creates iteration loops:

1. Traditional for loop: `for (initialization; condition; update)`
2. Enhanced for loop (foreach): `for (type variable : collection)`

---

### **22. `goto`**

The `goto` keyword is reserved but not used in Java.

- Originally intended for unconditional jumps.
- Java uses structured programming constructs instead.

---

### **23. `if`**

The `if` keyword creates conditional statements.

- Executes code blocks based on boolean expressions.
- Can be combined with `else` and `else if` for complex conditions.

---

### **24. `implements`**

The `implements` keyword allows a class to implement one or more interfaces.

- The class must provide implementations for all abstract methods in the interface.
- A class can implement multiple interfaces.

---

### **25. `import`**

The `import` keyword includes external classes and packages.

- Makes classes from other packages available without fully qualified names.
- Static imports allow importing static members directly.

---

### **26. `instanceof`**

The `instanceof` keyword tests if an object is an instance of a specific class or interface.

- Returns `true` if the object is an instance of the specified type.
- Also returns `true` for parent classes and implemented interfaces.

---

### **27. `int`**

The `int` keyword declares a 32-bit signed integer variable.

- Range: -2,147,483,648 to 2,147,483,647.
- Default value: 0.
- Wrapper class: `Integer`.

---

### **28. `interface`**

The `interface` keyword defines an interface.

- Interfaces specify method signatures that implementing classes must provide.
- Can contain default methods, static methods, and constants.

---

### **29. `long`**

The `long` keyword declares a 64-bit signed integer variable.

- Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.
- Default value: 0L.
- Wrapper class: `Long`.

---

### **30. `native`**

The `native` keyword indicates that a method is implemented in platform-specific code.

- The method implementation is written in another language (usually C or C++).
- Used for system-level operations and performance-critical code.

---

### **31. `new`**

The `new` keyword creates new objects or arrays.

- Allocates memory for the object and calls the constructor.
- Returns a reference to the newly created object.

---

### **32. `package`**

The `package` keyword declares the package to which a class belongs.

- Must be the first non-comment line in a Java source file.
- Provides namespace organization and access control.

---

### **33. `private`**

The `private` keyword is an access modifier.

- Makes members accessible only within the same class.
- Provides the highest level of encapsulation.

---

### **34. `protected`**

The `protected` keyword is an access modifier.

- Makes members accessible within the same package and by subclasses.
- Provides package-level access plus inheritance access.

---

### **35. `public`**

The `public` keyword is an access modifier.

- Makes members accessible from anywhere in the program.
- Provides the lowest level of encapsulation.

---

### **36. `return`**

The `return` keyword exits a method and optionally returns a value.

- In void methods: Simply exits the method.
- In non-void methods: Must return a value of the declared return type.

---

### **37. `short`**

The `short` keyword declares a 16-bit signed integer variable.

- Range: -32,768 to 32,767.
- Default value: 0.
- Wrapper class: `Short`.

---

### **38. `static`**

The `static` keyword creates class-level members.

- Static variables belong to the class rather than instances.
- Static methods can be called without creating an object.
- Static blocks execute when the class is first loaded.

---

### **39. `strictfp`**

The `strictfp` keyword ensures portable floating-point calculations (added in Java 1.2).

- Forces floating-point operations to adhere to IEEE 754 standards.
- Can be applied to classes, interfaces, or methods.

---

### **40. `super`**

The `super` keyword refers to the parent class.

- Accesses parent class constructors, methods, and variables.
- Must be the first statement when calling parent constructors.

---

### **41. `switch`**

The `switch` keyword creates multi-branch conditional statements.

- Evaluates an expression and matches it against case labels.
- More efficient than multiple if-else statements for many conditions.

---

### **42. `synchronized`**

The `synchronized` keyword provides thread safety.

- Can be applied to methods or code blocks.
- Ensures only one thread can execute the synchronized code at a time.

---

### **43. `this`**

The `this` keyword refers to the current object instance.

- Differentiates between instance variables and parameters with the same name.
- Can be used to call other constructors in the same class.

---

### **44. `throw`**

The `throw` keyword manually throws an exception.

- Can throw both checked and unchecked exceptions.
- Must be followed by an exception object.

---

### **45. `throws`**

The `throws` keyword declares that a method may throw specific exceptions.

- Listed in the method signature after the parameter list.
- Required for checked exceptions that are not caught within the method.

---

### **46. `transient`**

The `transient` keyword excludes variables from serialization.

- Transient variables are not saved when an object is serialized.
- Their values are not restored during deserialization.

---

### **47. `try`**

The `try` keyword defines a block where exceptions may occur.

- Must be followed by at least one `catch` or `finally` block.
- Try-with-resources automatically manages resource cleanup (Java 7+).

---

### **48. `void`**

The `void` keyword indicates that a method does not return a value.

- Used as the return type for methods that perform actions without returning data.
- Cannot be used as a variable type.

---

### **49. `volatile`**

The `volatile` keyword ensures variable visibility across threads.

- Prevents compiler optimizations that might cache variable values.
- Guarantees that reads and writes are directly from/to main memory.

---

### **50. `while`**

The `while` keyword creates loops that continue while a condition is true.

- The condition is evaluated before each iteration.
- If the condition is initially false, the loop body never executes.

---

## Additional Literals (Not Keywords)

### **`true`**

Boolean literal representing the true value.

### **`false`**

Boolean literal representing the false value.

### **`null`**

Reference literal representing a null reference (no object).