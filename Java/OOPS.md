## Static var and instance var

static variables share the same copy, no matter how many object you create and try to access it.

```java
package StaticVar;

  

public class Demo {

    static int x = 10;

  

    static void display() {

        System.out.println(x);

    }

}

  

class Test {

    public static void main(String[] args) {

        Demo obj1 = new Demo();

        Demo obj2 = new Demo();

  

        ++obj1.x;

  

        System.out.println("X in object 1");

        obj1.display();

        System.out.println("X in object 2");

        obj2.display();

    }

}
```

instance variable will have different copy for every object created.

```java
package InstanceVar;

  

public class Demo {

    int x = 10;

  

    void display() {

        System.out.println(x);

    }

}

  

class Test {

    public static void main(String[] args) {

        Demo obj1 = new Demo();

        Demo obj2 = new Demo();

  

        ++obj1.x;

  

        System.out.println("X in object 1");

        obj1.display();

        System.out.println("X in obj 2");

        obj2.display();

  

    }

}
```

## instance variables and instance methods 
if a variable is a part of a class it will be a instance variable, and the behaviours of the class or the methods will be instance methods.

```java
Instance obj = new Instance(); 
```
here obj is a reference variable because this line new Instance() created a object of the class Instance in the heap memory and the obj is the reference to that object.

new keyword allows dynamic memory allocation, allocating memory at runtime

**Instantiation** means **creating an object of a class** using the `new` keyword.  
This process **dynamically allocates memory** for the object **in the heap memory** during runtime.

for accessing the properties fields behavoiurs methods we use . operator

## Class vs Objects

- **Class**: A **blueprint** or **template** for creating objects. It defines **properties (attributes)** and **behaviors (methods)**.
- **Object**: A **real, usable entity** created based on the class. It is an **instance** of the class, meaning it has actual values for the properties defined in the class and can perform the behaviors.

## this keyword

what i understood is that i can return object for current class
When you use `return this;` inside a method, you're returning the **current object** — that is, the current instance of the class the method was called on.

```java
package ThisKeyword;

  

public class This {

    int noOfWheel;

    float currentFuel;

    String color;

    float maxSpeed;

    int noOfSeats; // instance variables or properties

  

    public This drive() {

        System.out.println("Car is driving");

        currentFuel--;

        return this;

    }

  

    public void addFuel(float fuel) {

        currentFuel += fuel;
        this.currentFuel += fuel;

    }

  

    public float getCurrentFuelLevel() {

        return currentFuel;

    }

  

    public static void main(String[] args) {

        This obj = new This();

        obj.currentFuel = 103.0f;

        This car = obj.drive().drive().drive();

        car.addFuel(1.2f);

        float result = car.getCurrentFuelLevel();

        System.out.println(result);

    }

}
```

this is basically the reference to the object of present class when and object is created a reference is also created which can not be seen that is this only 
# I got to know one in objects syntax in java

lets say we have an instance method and we create an instance of an class then we can use the reference variable with the methods name like this if we want to call it multiple times

```java
obj.methodName().methodName().methodName()
```

I found this so dope man this is known as `method-chaining`.
# static
we already know that static variables belong to class every instance of a class created can use it with the same copy for other instances of the class and methods is just you can use it without creating the object also static members cannot directly access the non static members of a class also there is a static code block that is executed only once when a class is loaded also ==one thing is that may be we cannot access non static members of a class using static things but we can access them through the instance.== Inner classes can also be static 

## Why This Matters

The `static` keyword for inner classes is about **relationship to the outer class**, not about accessing from static methods.

### Inner Class Rules:

- **Non-static inner class**: Needs an instance of the outer class to exist
- **Static inner class**: Can exist independently of the outer class

### Separate Class Rules:

- **Top-level classes**: Always independent, never need `static` keyword

```java
// Scenario 1: Non-static inner class
public class Main {
    static void staticMethod() {
        // To create non-static inner class from static context:
        Main mainObj = new Main();           // Need outer class instance first
        Students student = mainObj.new Students(); // Then create inner class
    }
    
    class Students { } // Non-static inner - tied to Main instance
}

// Scenario 2: Static inner class  
public class Main {
    static void staticMethod() {
        Students student = new Students(); // Direct creation - no outer instance needed
    }
    
    static class Students { } // Static inner - independent of Main instance
}

// Scenario 3: Separate class (your current code)
public class Main {
    static void staticMethod() {
        Students student = new Students(); // Direct creation - completely separate class
    }
}
class Students { } // Separate class - always independent
```

# Constructor

```java
package Challenge9;

  

public class Book {

    static int totalBooks;

    String title;

    String author;

    int isbn;

    boolean borrowBook = false;

  

    static {

        totalBooks = 0;

    }

  

    {

        totalBooks++;

    }

  

    Book() {

        title = "Unknown";

        author = "Unknown";

        isbn = 0;

    }

  

    Book(int isbn) {

        this.isbn = isbn;

        author = "Saad";

        title = "rdr";

    }

  

    Book(String title, String author, int isbn) {

        this.title = title;

        this.author = author;

        this.isbn = isbn;

    }

  

    static int getTotalNoOfBooks() {

        return totalBooks;

    }

  

    void borrowBook() {

        if (borrowBook) {

            System.out.println("Book is already borrowed");

        } else {

            borrowBook = true;

            System.out.println("Book borrowed");

        }

    }

  

    void returnBook() {

        if (borrowBook) {

            borrowBook = false;

            System.out.println("book returned");

        } else {

            System.out.println("Book is not borrowed");

        }

    }

  

    public static void main(String[] args) {

        Book obj = new Book();

        // obj.author = "Saif Ali Khan";

        // // obj.title = "MC";

        obj.isbn = 123;

        obj.borrowBook();

        System.out.println(obj.author + obj.title + obj.isbn);

        System.out.println(getTotalNoOfBooks());

        obj.returnBook();

    }

}
```

Constructor has same name as class it can be default or parameterized we cannot used this in a static reference because it does not has an instance but can use class name because static memebers are part of class we can also do constructor chaining 

```java
Book(int isbn) {

        this.isbn = isbn;

        author = "Saad";

        title = "rdr";

    }
    Book() {
      this("1"); // isbn
    }
```

# Code blocks

```java
static {
}
{

}
```

static code blocks execute only once the class gets loaded
normal code block will be executed everytime an instance is made.