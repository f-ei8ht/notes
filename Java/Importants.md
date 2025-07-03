
#note 
default value for reference is null

#imp
In **Java**, every variable that is **not explicitly initialized** will be assigned a **default value** by the JVM **only if** it is a **member (instance or static) variable**. Local variables **must be initialized** before use.

### ✅ Default Values of Data Types in Java

| **Data Type**                                   | **Default Value**         |
| ----------------------------------------------- | ------------------------- |
| byte                                            | 0                         |
| short                                           | 0                         |
| int                                             | 0                         |
| long                                            | 0L                        |
| float                                           | 0.0f                      |
| double                                          | 0.0d                      |
| char                                            | '\u0000' (null character) |
| boolean                                         | false                     |
| Object reference (like String, arrays, classes) | `null`                    |

# what happens if

| Case                           | Class Loaded (Method Area) | Object Created (Heap) | Memory Usage                      |
| ------------------------------ | -------------------------- | --------------------- | --------------------------------- |
| Empty `.java` file             | ❌ No                       | ❌ No                  | 0                                 |
| Empty class                    | ✅ Yes                      | ❌ No                  | Tiny (metadata only)              |
| Object of empty class created  | ✅ Yes                      | ✅ Yes                 | Metadata + 16–32 bytes per object |
| No object usage (null or none) | Maybe (if used elsewhere)  | ❌ No                  | Small to none                     |
it is a clean code practise to access the static members using the class name and dot operator

```java
public class Main {  
    static int x = 10;  
  
    public static void main(String[] args) {  
        System.out.println(Main.x);  
        System.out.println(Call.x);  
    }  
}  
  
class Call {  
    static int x = 11;  
    private Call() {  
        throw new IllegalArgumentException("Go to hell");  
    }  
}
```

# why we use constructor call in the object instantiation 

The constructor's main job is to **override those default values** with meaningful ones that you actually want.

to just over ride the default values, and assign the values you have given

#mostimp
the object is created in the heap when new is encountered by jvm with defualt values like null 0 but construcotr assigns the state given.
dynamic allocate it is runtime process which happens when new keyword is encountered means the memory will be allocated during the runtime 
#mostimp constructor is a special method which will have same name as class.

# the class swap problem

variables does not gets swap if you do this
```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        swap(a, b);
        System.out.println("a = " + a + ", b = " + b);  // Still a = 5, b = 10
    }

    public static void swap(int x, int y) {
        int temp = x;
        x = y;
        y = temp;
    }
}
```

this is because everything in java is pass by value, even the objects, and java tends to pass copy of the value to the x and y variables and not the reference of the variable a and b in the stack as swap is also a method so a new stack frame will be created with x and y which will match the value of as given to them from a to b

```java
class Box {
    int value;

    Box(int value) {
        this.value = value;
    }
}

public class Main {
    public static void main(String[] args) {
        Box a = new Box(10);
        Box b = new Box(20);

        System.out.println("Before swap:");
        System.out.println("a.value = " + a.value);
        System.out.println("b.value = " + b.value);

        swap(a, b);  // Will not work
        System.out.println("\nAfter swap (doesn't work):");
        System.out.println("a.value = " + a.value);
        System.out.println("b.value = " + b.value);

        swapValues(a, b);  // Will work
        System.out.println("\nAfter swapValues (field swap works):");
        System.out.println("a.value = " + a.value);
        System.out.println("b.value = " + b.value);
    }

    // ❌ This won't affect original references
    public static void swap(Box x, Box y) {
        Box temp = x;
        x = y;
        y = temp;
    }

    // ✅ This will swap the actual values inside the objects
    public static void swapValues(Box x, Box y) {
        int temp = x.value;
        x.value = y.value;
        y.value = temp;
    }
}

```

need to make your own wrapper to swap object values like this as the wrapper classes are immutable they are final


final variable initialize when

|Scope|Must be initialized when?|
|---|---|
|Local|Before use — either at declaration or later|
|Instance `final`|At declaration or in constructor|
|Static `final`|At declaration or in static block|