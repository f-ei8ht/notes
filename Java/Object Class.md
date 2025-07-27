The object class is the parent class of all classes in java, forming the top of the class hierarchy.
it provides equals(), hashCode(), toString(), getclass() that can be overriden by subclasses.
# Java `Object` Class Overview

In Java, the most commonly required methods for any object—whether it's predefined or customized—are encapsulated into a separate class, which is the `java.lang.Object` class.

## Key Points

1. **Object class is the root (superclass) of all Java classes.**  
   - Its methods are available to every Java class by default.

2. **Inheritance from Object class:**  
   - If a class does **not** extend any other class, it is a **direct child** of `Object`.
   - If a class **does** extend another class, it is an **indirect child** of `Object`.

---

## Methods in `java.lang.Object` Class

| No. | Method Signature                                                                 |
|-----|----------------------------------------------------------------------------------|
| 1   | `public String toString();`                                                     |
| 2   | `public native int hashCode();`                                                 |
| 3   | `public boolean equals(Object o);`                                              |
| 4   | `protected native Object clone() throws CloneNotSupportedException;`            |
| 5   | `public final Class<?> getClass();`                                             |
| 6   | `protected void finalize() throws Throwable;`                                   |
| 7   | `public final void wait() throws InterruptedException;`                         |
| 8   | `public final native void wait() throws InterruptedException;`                  |
| 9   | `public final void wait(long ms, int ns) throws InterruptedException;`          |
| 10  | `public final native void notify();`                                            |
| 11  | `public final native void notifyAll();`                                         |

---

> 📌 These methods play a key role in object representation, comparison, cloning, synchronization, and garbage collection.

---


# `clone()` Method in Java

## What is Cloning?

1. **Cloning** is the process of creating an **exact duplicate** of an object.
    
2. The main objective of cloning is to maintain **backup purposes**.
    
    > If something goes wrong, we can recover the situation using the backup copy.
    
3. Cloning can be performed using the `clone()` method of the `Object` class.
    

## Method Signature

```
protected native Object clone() throws CloneNotSupportedException;
```

## Example: Cloning in Action

```java
class Test implements Cloneable {
    int i = 10;
    int j = 20;

    public static void main(String[] args) throws CloneNotSupportedException {
        Test t1 = new Test();
        Test t2 = (Test) t1.clone();

        t2.i = 888;
        t2.j = 999;

        System.out.println(t1.i + "---------------" + t1.j);
        System.out.println(t2.i + "---------------" + t2.j);
    }
}
```

### Output:

```
10---------------20
888---------------999
```

## Notes on Cloning

- Cloning can be performed **only on Cloneable objects**.
    
- An object is said to be **Cloneable** **only if** its class **implements the** `**Cloneable**` **interface**.
    
- `Cloneable` is a **marker interface** in `java.lang` package:
    
    - It does **not contain any methods**.
        
    - It signals the JVM that the class allows cloning.
        

### Important:

- If we try to clone an object that **does not implement** `Cloneable`, a **CloneNotSupportedException** will be thrown at runtime.

---
