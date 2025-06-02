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