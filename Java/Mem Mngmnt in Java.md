Memory Management is done by jvm

## Stack in java
in stack we store primitives and the temporary variables, we can also see a seprate memory frame for the methods in side the stack. that is the stack frame also we can store the reference variables like 
```java
Demo obj = new Demo(); // here obj is the reference variable
```

each thread will have its own stack memory but will share a single heap memory stack follows Last In and First Out order of pushing popping

We also have some thing like call stack which manages methods call and has stack frame that stores things related to the method.

We can have StackOverFlowError

## Heap in Java
in heap we store objects, array, string, interface, It is dynamically allocated during program execution, it uses garbage collector to freed up after the function execution finishes up. 
heap is not structured every thread will share the same heap memory 

we can se OutOfMemoryError 

Lets take an example to understand memory management

```java
public class MemoryManagement {
	public static void main(String[] args) {
		int primitiveVariable1 = 10;
		MemoryManagement mobj1 = new MemoryManagement();
		String stringLiteral = "24";
		MemoryManagement mobj2 = new MemoryManagement();
		System.out.println(System.identityHashCode(primitiveVariable1));
		System.out.println(mobj1);
		System.out.println(mobj2);
		System.out.println(System.identityHashCode(stringLiteral));
		System.out.println("-------------From the method main----------");
		mobj1.memoryManagementTest(mobj2); //calling of fn passing obj ref
	}

	private void memoryManagementTest(MemoryManagement obj) {
		MemoryManagement obj3 = obj;
		String stringLiteral2 = "24";
		String stringLiteral3 = new String("24");
		String stringLiteral4 = new String("24");
		stringLiteral4 = stringLiteral4.intern();
		System.out.println(obj);
		System.out.println(obj3);
	    System.out.println(System.identityHashCode(stringLiteral2));
		System.out.println(System.identityHashCode(stringLiteral3));
		System.out.println(System.identityHashCode(stringLiteral4));
	}
}
```

```bash
Output:

1926375211
MemoryManagement@33cb5951
MemoryManagement@365c30cc
1881129850
-------------From the method main----------
MemoryManagement@365c30cc
MemoryManagement@365c30cc
1881129850
1095293768
1881129850
```

![Memory Management](Memory.png)

## Detailed Explanation

1. First we have the `main()` function that will be looked upon by the JVM and in stack JVM will create a stack frame for it.
2. Then a integer variable will be pushed into it.
3. Then a mobj1 (reference variable) to the object of the class MemoryManagement will be pushed in to stack and reference to the object created using the `new` keyword will be created in the heap.
4. Then a stringLiteral will be pushed which will have the reference of the string "24" in String constant pool.
5. Then a mobj2 (reference variable) to the a new object of the class MemoryManagement will be pushed in to the stack and reference to the newly created object using the `new` keyword will be created in the heap as well.
6. `mobj1.memoryManagementTest(mobj2);` then we have this line we know that to access non static members of a class we have to create object and we need to use the reference variable with the dot operator to access we will pass the reference variable of the other object created in the heap in the method.
7. Which will then create a new stack frame in the stack and firstly we have a parameter `obj` which will be pushed into the stack, then obj3, we see that the reference is same in both obj, mobj2, obj3, so they will refer to the same object in the heap.
8. Then we have stringLiteral2, strinLiteral3, and stringLiteral4 that will be pushed into the stack one by one.
9. stringLiteral1 and stringLiteral2 will point to the same string "24" in the SCP,  but string Literal3 is created using the `new` keyword so it will not be in the SCP, it will be created as an object in the heap.
10. in stringLiteral4 we assigned the variable again with adding .intern() method that will point to the string in the basically it returns the reference but if we assign then it will point to the same.

## Strong Reference and Soft Reference and Weak Reference

### Strong Reference
Default type of reference to objects

```java
MyClass obj = new MyClass();
```

I think the object is not available for garbage collection until unless it does not points to null or the reference becomes out of scope from the stack and the object does not points to any other references.

### Weak Reference

Weak reference is to be specified the object is available for garbage collected as soon as the GC is ran or  I think if that does not points to any strong/hard reference. 
```java
import java.lang.ref.WeakReference;

  

public class MemoryManagement {

    static MemoryManagement obj; // Now accessible everywhere in class

  

    public static void main(String[] args) {

        obj = new MemoryManagement();

        WeakReference<MemoryManagement> weak = new WeakReference<>(obj);

        System.out.println(weak.get());

        test(); // call test to use obj

        obj = null;

    }

  

    public static void test() {

        System.out.println("In test(): " + obj); // Now you can use obj

    }

}
```

we can see here we have a weak reference but we also have a strong/hard reference as well which will not allow gc to collect the object but as soon as we make it null it will become available for gc.

### Soft Reference

soft reference is a type of weak reference but gc will only collect the object if and only if it has an urgent need to save memory from being or giving the error outofmemoryeroor means the memory is going to be full.

```java
import java.lang.ref.SoftReference;

public class SoftReferenceExample {
    public static void main(String[] args) {
        // Create a strong reference
        String strong = new String("Soft reference object");

        // Create a soft reference to the same object
        SoftReference<String> softRef = new SoftReference<>(strong);

        // Remove the strong reference
        strong = null;
    }
}

```

this will get cleared only when their is memory pressure

### Phantom Reference
**PhantomReference** is a special tool in Java that tells you when an object is about to be deleted, so you can clean up safely — but it won’t let you use the object again.

## Garbage Collector

Automatic garbage collection by managed by jvm in the background, It is basically for claiming memory, meaning objects that are no longer reachable or objects that are no longer have any active reference. garbage collection is expensive 

their are many types of gc 
1. serial gc
2. parallel gc [default in java 8]
3. g1gc garbage first [default in java 11 and java 17]
4. z gc
5. Concurrent Mark Sweep
6. Shenandoah GC
   
Garbage collector can be called using System.gc();

We can also see a method called `finalize()` deprecated from java 9 and removed in java 18 what it does it it lets the object clean up resources just before being deleted by gc or just before reclaiming the space it is defined in object class and we need to override it to use explicitly it may or may not run up to jvm allowed once per object.

```java
public class Test {
    @Override
    public void finalize() throws Throwable {
    }
}
```
