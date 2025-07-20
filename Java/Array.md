- Array is contiguous memory allocation of similar elements or data types
- how we can make 1d array in java

```java

int size = 100;
int a[] = new int[size];

int a[] = new int[100];

int[] a = new int[100];

int[] a = {1,2,3,4,5};

int a[];
a = new int[5];

a[0] = 3;
a[1] = 4;

```

- array is a linear data structure

```java
int [][] a = new int[2][2];
```

the memory given to will not depend on the value but on the number of elements given in the above example we have 2 and 2 that is 4 and for int we have 4 bytes so 4 * 4 it is 16 bytes 

# Java Array Declaration Summary

## # 1D Array Declaration (`int[]`)

All of the following are **valid** ways to declare a 1D `int` array:

```java
int[] a;    // ✅ Recommended - clear separation of type and name
int []a;    // ✅ Valid but spacing is less clear
int a[];    // ✅ Valid but not preferred in Java (C-style)
```

⛔ **Invalid**: Size can't be specified during declaration:

```java
int[5] a;   // ❌ Compile-time Error
```

---

## # 2D Array Declaration (`int[][]`)

All 6 declarations below are **valid** 2D arrays:

```java
int[][] a;
int [][]a;
int a[][];
int[] []a;
int[] a[];
int []a[];
```

---

## # 3D Array Declaration (`int[][][]`)

All 10 declarations below are **valid** 3D arrays:

```java
int[][][] a;
int [][][]a;
int a[][][];
int[] [][]a;
int[] a[][];
int[] []a[];
int[][] []a;
int[][] a[];
int []a[][];
int [][]a[];
```

---

## # Multiple Variable Declarations

### # Example 1:

```java
int[] a1, b1;
```

- `a1` → 1D array
    
- `b1` → 1D array  
    ✅ **Valid**
    

---

### # Example 2:

```java
int[] a2[], b2;
```

- `a2` → 2D array (`int[][]`)
    
- `b2` → 1D array (`int[]`)  
    ✅ **Valid**
    

---

### # Example 3:

```java
int[][] a3, b3;
```

or

```java
int[] []a3, b3;
```

- Both `a3` and `b3` → 2D arrays  
    ✅ **Valid**
    

---

### # Example 4:

```java
int[] a, []b;
```

- ❌ **Invalid**
    
- Error: `[]b` is not allowed. Brackets before variable name only work for the **first** variable.
    

---

## # Important Rule

> If you're using bracket notation `[]` before variable names (like `int[] a`), this is only allowed for the **first** variable in the declaration. Others must follow regular syntax.

---

## # Summary Table

|Declaration|Meaning|Valid?|
|---|---|---|
|`int[] a1, b1;`|Both 1D arrays|✅|
|`int[] a2[], b2;`|a2 → 2D, b2 → 1D|✅|
|`int[][] a3, b3;`|Both 2D arrays|✅|
|`int[] a, []b;`|❌ Invalid (bad syntax)|❌|

---

|Java Type|Internal Class Name|
|---|---|
|`int[]`|`[I`|
|`int[][]`|`[[I`|
|`int[][][]`|`[[[I`|
 at the time of array creation we should specify the size other wise compile error

the size can be byte short int and char only new int[this size]
2147483647 => maximum allowed size int max
defualt value comes in if we do not specify any value

- `int[][]` is an array of **references** to `int[]` `int[]a = new int[2]`
- By default, all reference-type array elements are `null`
- Primitive `int` values get `0`, but `int[]` (an object) gets `null` if uninitialized
- then if we access `a[0][0]`this is npe because we cannot load a null `a[0]` 

#  1. Jagged Array (Irregular Multidimensional Array)

A jagged array is a 2D or 3d array where each row can have a different number of columns.

### ✅ Java Example:
```java
public class JaggedArrayExample {
    public static void main(String[] args) {
        // Declare a jagged array
        int[][] jagged = new int[3][];
        
        // Initialize each row with different length
        jagged[0] = new int[]{1, 2};
        jagged[1] = new int[]{3, 4, 5};
        jagged[2] = new int[]{6};

        // Print the jagged array
        for (int i = 0; i < jagged.length; i++) {
            for (int j = 0; j < jagged[i].length; j++) {
                System.out.print(jagged[i][j] + " ");
            }
            System.out.println();
        }
    }
}
### 📌 Output:

`1 2 3 4 5 6`

```

# 2. Anonymous Array

An anonymous array is created and used without assigning it to a variable. It's often used in method calls. we cannot specify size we will get compile time error.

```java
public class AnonymousArrayExample {
    public static void main(String[] args) {
        // Pass anonymous array directly to method
        printSum(new int[]{10, 20, 30});
    }

    public static void printSum(int[] numbers) {
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        System.out.println("Sum: " + sum);
    }
}

```

| Feature         | Jagged Array                               | Anonymous Array                            |
| --------------- | ------------------------------------------ | ------------------------------------------ |
| **Structure**   | 2D array with varying row lengths          | 1D array used without a name               |
| **Use Case**    | Storing non-uniform data (like table rows) | One-time use (method argument, loop, etc.) |
| **Declaration** | `new int[3][]` + initialize each row       | `new int[]{1, 2, 3}`                       |

for primitive types we can specify like for int we can have array elements that can be int byte short and char

for float i think we can have int byte short char and float

In the case of Object type arrays as array elements we can provide either declared type objects or its child class objects. 
Example 1: Object[] a=new Object[10]; 
a[0]=new Integer(10);//(valid)
a[1]=new Object();//(valid) 
a[2]=new String("bhaskar");//(valid) 
Example 2: Number[] n=new Number[10]; 
n[0]=new Integer(10);//(valid) 
n[1]=new Double(10.5);//(valid) 
n[2]=new String("bhaskar");//C.E:incompatible types//(invalid)

for interface implemented class objects allowed

for abstract class child class objects allowed

we cannot convert arrays at the object level but the elements can be as they are primitives

Note: In the case of object type arrays child type array can be assign to parent type array variable. Example: String[] s={"A","B"}; Object[] o=s;

int[] a = {1,2};  
int[] b = {1,2,3};  
b=a;

reference changes the size does not matters here and the copying wont happen here

Whenever we are assigning one array to another array dimensions must be matched that is in the place of one dimensional array we should provide the same type only otherwise we will get compile time error.

Example: int[][] a=new int[3][]; a[0]=new int[4][5];//C.E:incompatible types(invalid) a[0]=10;//C.E:incompatible types(invalid) a[0]=new int[4];//(valid

Note: Whenever we are performing array assignments the types and dimensions must be matched but sizes are not important. Example 1: int[][] a=new int[3][2]; a[0]=new int[3]a[1]=new int[4]; a=new int[4][3];

Once we created an array every element is always initialized with default values irrespective of whether it is static or instance or local array