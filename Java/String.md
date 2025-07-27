strings are nothing but group of characters 

in c/c++ a string is represented as an array of characters where the last character will be '\0'
which is a null character, and this last character represents the end of string 

But in java a string is an object of String class and it can also be used as a data type becuase class can act as user-defined datatypes.

## String Creation
String can be created using these ways

```java
String s;
s = "saif";

String s = "saif";

String s = new String("Saif");

char[] arr = {'s','a', 'i', 'f'};
String s = new String(arr);

String s = new String(arr, 2,3); // we can also define the offset and count 
```

## String Immutability

Strings in java are immutable that is we cannot change or manipulate a string object when ever we try to do so a new object is created
#Existing string can never be changed.
```java
package Strings;

  

public class Str {

    public static void main(String[] args) {

        String a = "saif";

        String b = "ali";

        String c = a + b;

        String d = "saifali";

        System.out.println("a: " + a);

        System.out.println("b: " + b);

        System.out.println("c: " + c);

        System.out.println("d: " + d);

        System.out.println(a == b); // false

        System.out.println((a + b).intern() == c.intern()); // true

        System.out.println(c.intern() == d); // true

        System.out.println(c.equals(d)); // true

        System.out.println(d.equals(c)); // true

        System.out.println(c.equals(a + b)); // true

        System.out.println((a + b).equals(c)); // true

    }

}
```

lets say we have String a = "saif" and we do like a = a + "ali"; so a new object will be created and this reference of this object or now the literal a will point to this object instead of the saif one earlier

== always compares the reference not the value a object holds for that we can use .equals()

and as being immutable string can hold more memory when kept modified.

I think so what goes to pool that is known at compile time but what will be known at runtime will go to the heap so when we use concatenation it happens at runtime and the internal working of concatenation using + includes new `StringBuilder().append()`, so yeah they will not go to the pool. I guess!!!!

# Strings are slow so we avoid using the concatenation and looping in it to modify everytime or add some other string so we have two solutions

# Solution 1 
## String.format and printf()
```java
package Strings;

  

public class StringPrintf {

    public static void main(String[] args) {

        int num = 1234;

        double price = 19.99;

        String name = "Product";

  

        // These produce identical formatting:

        String formatted = String.format("%-15s: $%8.3f (ID: %04d)", name, price, num);

        System.out.printf("%-15s: $%8.3f (ID: %05d)%n", name, price, num);

  

        // Output: "Product : $ 19.99 (ID: 1234)"

        System.out.println(formatted);

    }

}
```

## The Format String: `"%-15s: $%8.2f (ID: %04d)"`

Let me explain each format specifier:

### `%-15s` (for name)

- `%s` = String format specifier
- `-` = **Left-align flag** (without this, it would be right-aligned)
- `15` = **Width** - reserve 15 characters total
- Result: `"Product "` (Product + 8 spaces to make 15 total)

### `%8.2f` (for price)

- `%f` = Floating-point format specifier
- `8` = **Width** - reserve 8 characters total (including decimal point and digits)
- `.2` = **Precision** - show exactly 2 decimal places
- No `-` flag = **Right-aligned** (default)
- Result: `" 19.99"` (3 spaces + 19.99 to make 8 total)

### `%04d` (for num)

- `%d` = Decimal integer format specifier
- `0` = **Zero-padding flag** - pad with zeros instead of spaces
- `4` = **Width** - make it 4 characters total
- Result: `"1234"` (already 4 digits, so no padding needed)

## Step-by-Step Formatting


```bash
"%-15s: $%8.2f (ID: %04d)"
    ↓      ↓         ↓
"Product        : $   19.99 (ID: 1234)"
```

1. `%-15s` → `"Product "` (15 chars, left-aligned)
2. `": $"` → `": $"` (literal text)
3. `%8.2f` → `" 19.99"` (8 chars total, 2 decimal places, right-aligned)
4. `" (ID: "` → `" (ID: "` (literal text)
5. `%04d` → `"1234"` (4 chars, zero-padded)
6. `")"` → `")"` (literal text)

## Visual Breakdown

```bash
Product        : $   19.99 (ID: 1234)
├─────────────┤    ├──────┤     ├──┤
15 chars           8 chars     4 chars
left-aligned       right-align  zero-pad
```

## Flag Summary Used Here

- `%-` = Left-align
- `0` = Zero-padding
- `.2` = Precision (2 decimal places)
- `8`, `15`, `4` = Width specifications

## The `%n` in printf

java

```java
System.out.printf("%-15s: $%8.2f (ID: %04d)%n", name, price, num);
```

- `%n` = Platform-independent newline (better than `\n`)

This creates professional-looking, aligned output that's commonly used in reports, receipts, or formatted displays.

# Solution 2

We can use StringBuilders or StringBuffer but mostly we use StringBuilders only

### 🔍 Detailed Comparison Table: `String` vs `StringBuilder` vs `StringBuffer`

| Feature             | `String`                                                                 | `StringBuilder`                                                               | `StringBuffer`                                                               |
| ------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Mutability**      | ❌ Immutable (cannot be changed after creation)                           | ✅ Mutable (can be modified without creating new object)                       | ✅ Mutable (same as `StringBuilder`)                                          |
| **Thread Safety**   | ✅ Yes (immutable, so thread-safe by nature)                              | ❌ No (not synchronized, not safe in multi-threaded context)                   | ✅ Yes (all methods synchronized)                                             |
| **Speed**           | ❌ Slow for concatenation and modification (creates new object each time) | ✅ Fastest for frequent changes in **single-threaded** programs                | ⚠️ Slower than `StringBuilder` due to synchronization overhead               |
| **Storage**         | Literals stored in **String Pool**; new objects stored in **Heap**       | Always stored in **Heap**                                                     | Always stored in **Heap**                                                    |
| **Best Use Case**   | Use when data is **fixed or rarely changes**                             | Use when you do **a lot of string modifications** in **single-threaded** code | Use when you do **a lot of modifications** in **multi-threaded** environment |
| **Synchronization** | ✅ Not needed (because immutable)                                         | ❌ Not synchronized — use manually if needed                                   | ✅ Built-in synchronization for all methods                                   |
| **Performance Tip** | Avoid in loops for concatenation                                         | ✅ Recommended in loops for fast modification                                  | ⚠️ Use only when thread safety is needed — otherwise use `StringBuilder`     |
in String Buffer we have equals from the object class only

when we use String s = new String("HELLO")

we get a s -> point to HELLO in heap but there is also HELLO in SCP created if it was not present. but String s = "HELLO"; this will always point in scp no heaping here and scp also does not allows duplicate objects

Because runtime operation if there is a change in content with those changes a new object will be created only on the heap but not in SCP. If there is no change in content no new object will be created the same object will be reused. This rule is same whether object present on the Heap or SCP

Garbage collector can't access SCP area hence even though object doesn't have any reference still that object is not eligible for GC if it is present in SCP.

All SCP objects will be destroyed at the time of JVM shutdown automatically.

1. In our program if any String object is required to use repeatedly then it is not recommended to create multiple object with same content it reduces performance of the system and effects memory utilization. '
2. We can create only one copy and we can reuse the same object for every requirement. This approach improves performance and memory utilization we can achieve this by using "scp".

we use intern() to point the string object to scp if it was pointing to the object in heap and if the object not present then intern will create it in scp and point to it

String class constructors : 
1. String s=new String();  Creates an empty String Object.
2. String s=new String(String literals); To create an equivalent String object for the given String literal on the heap. 
3. String s=new String(StringBuffer sb); Creates an equivalent String object for the given StringBuffer. 
4. String s=new String(char[] ch); creates an equivalent String object for the given char[ ] array. Example: class StringDemo { public static void main(String[] args) { char[] ch={'a','b','c'} ; String s=new String(ch); System.out.println(ch);//abc } } 
5. String s=new String(byte[] b); Create an equivalent String object for the given byte[] array. Example: class StringDemo { public static void main(String[] args) {  byte[] b={100,101,102}; String s=new String(b); System.out.println(s);//def } }

# Methods

1. public char charAt(int index); Returns the character locating at specified index.
2. public String concat(String str) + += meant for concat only
3.  public boolean equals(Object o); For content comparison where case is important. It is the overriding version of Object class .equals() method
4.  public boolean equalsIgnoreCase(String s); For content comparison where case is not important
5. public String substring(int begin); Return the substring from begin index to end of the string (int begin, int end - 1)
6. public int lenght() -> returns length of characters
7. public String replace(char old, char new); To replace every old character with a new character.
8. public String toLowerCase(); Converts the all characters of the string to lowercase 
9. public String toUpperCase(); Converts the all characters of the string to capital letters
10. public String trim(); We can use this method to remove blank spaces present at beginning and end of the string but not blank spaces present at middle of the String
11. public int indexOf(char ch); It returns index of 1st occurrence of the specified character if the specified character is not available then return -1
12. public int lastIndexOf(Char ch); It returns index of last occurrence of the specified character if the specified character is not available then return -1





# Java: String vs StringBuffer vs StringBuilder

## ❌ When Not to Use `String`

1. If the content will change frequently, `String` is not recommended because it creates a **new object** for every change.
    
2. This is inefficient in terms of memory and performance.
    

## ✅ Use `StringBuffer` When:

- The content changes frequently **and** thread safety **is required**.
    
- All changes happen on the **same object** (no new object creation).
    

### Constructors of `StringBuffer`

1. `StringBuffer sb = new StringBuffer();`
    
    - Default capacity: `16`
        
    - If exceeded, new capacity is calculated as: `(currentCapacity + 1) * 2`
        
    
    ```java
    StringBuffer sb = new StringBuffer();
    System.out.println(sb.capacity()); // 16
    sb.append("abcdefghijklmnop");
    System.out.println(sb.capacity()); // 16
    sb.append("q");
    System.out.println(sb.capacity()); // 34
    ```
    
2. `StringBuffer sb = new StringBuffer(int initialCapacity);`
    
    ```java
    StringBuffer sb = new StringBuffer(19);
    System.out.println(sb.capacity()); // 19
    ```
    
3. `StringBuffer sb = new StringBuffer(String s);`
    
    - Capacity: `s.length() + 16`
        
    
    ```java
    StringBuffer sb = new StringBuffer("ashok");
    System.out.println(sb.capacity()); // 21
    ```
    

---

## Important Methods of `StringBuffer`

### Basic Info

- `int length()` → Number of characters.
    
- `int capacity()` → Total allocated capacity.
    
- `char charAt(int index)` → Returns character at index.
    
- `void setCharAt(int index, char ch)` → Replaces character at index.
    

### Append (Overloaded)

```java
sb.append(String);
sb.append(int);
sb.append(long);
sb.append(double);
sb.append(boolean);
sb.append(float);
sb.append(Object);
```

**Example:**

```java
StringBuffer sb = new StringBuffer();
sb.append("PI value is :");
sb.append(3.14);
sb.append(" this is exactly ");
sb.append(true);
System.out.println(sb); // PI value is :3.14 this is exactly true
```

### Insert (Overloaded)

```java
sb.insert(int index, String);
sb.insert(int index, int);
sb.insert(int index, long);
sb.insert(int index, double);
sb.insert(int index, boolean);
sb.insert(int index, float);
sb.insert(int index, Object);
```

**Example:**

```java
StringBuffer sb = new StringBuffer("abcdefgh");
sb.insert(2, "xyz");
sb.insert(11, "9");
System.out.println(sb); // abxyzcdefgh9
```

### Delete

```java
sb.delete(int begin, int end);
sb.deleteCharAt(int index);
```

**Example:**

```java
StringBuffer sb = new StringBuffer("saicharankumar");
sb.delete(6, 13);
System.out.println(sb); // saichar
sb.deleteCharAt(5);
System.out.println(sb); // saichr
```

### Reverse

```java
sb.reverse();
```

**Example:**

```java
StringBuffer sb = new StringBuffer("ashokkumar");
System.out.println(sb.reverse()); // ramukkohsa
```

### Length and Capacity Management

- `setLength(int length)` → Truncates or extends the length.
    
- `trimToSize()` → Removes unused capacity.
    
- `ensureCapacity(int minCapacity)` → Ensures capacity.
    

**Example:**

```java
StringBuffer sb = new StringBuffer("ashokkumar");
sb.setLength(6);
System.out.println(sb); // ashokk

StringBuffer sb2 = new StringBuffer(1000);
sb2.append("ashok");
sb2.trimToSize();
System.out.println(sb2.capacity()); // 5

StringBuffer sb3 = new StringBuffer();
sb3.ensureCapacity(1000);
System.out.println(sb3.capacity()); // 1000
```

---

## 🌐 StringBuilder (Java 1.5+)

- Same as `StringBuffer` but **not synchronized**.
    
- Better performance in **single-threaded** scenarios.
    

### StringBuffer vs StringBuilder

|Feature|String|StringBuffer|StringBuilder|
|---|---|---|---|
|Mutability|Immutable|Mutable|Mutable|
|Thread-safe|Yes (by default)|Yes|No|
|Performance|Low (new object)|Medium (synchronized)|High (non-sync)|
|Use-case|Fixed content|Changing w/ threads|Changing no threads|

---

## 🔁 Final Choice:

- **Use `String`**: If content is **fixed** and doesn’t change.
    
- **Use `StringBuffer`**: If content changes **frequently** and **thread safety** is needed.
    
- **Use `StringBuilder`**: If content changes **frequently** and **no thread safety** is needed.
    

---

## 📌 Additional String Methods

### ✅ `startsWith(String prefix)`

- Checks if string starts with a prefix.
    

```java
String s = "HelloWorld";
s.startsWith("Hello"); // true
```

### ✅ `endsWith(String suffix)`

- Checks if string ends with a suffix.
    

```java
String s = "HelloWorld";
s.endsWith("World"); // true
```

### ✅ `split(String regex)`

- Splits the string by a delimiter.
    

```java
String s = "apple,banana,mango";
String[] fruits = s.split(",");
```

### ✅ `getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)`

- Copies characters from string to destination char array.
    

```java
String s = "JavaProgramming";
char[] arr = new char[10];
s.getChars(4, 14, arr, 0);
System.out.println(arr); // Programming
```

### ✅ `compareTo(String anotherString)`

- Lexicographical comparison.
- Returns:

- `0` → equal
    
- `<0` → current string is less
    
- `>0` → current string is greater
    

```java
"abc".compareTo("xyz"); // -23
```

### ✅ `compareToIgnoreCase(String anotherString)`

- Ignores case while comparing.
    

```java
"abc".compareToIgnoreCase("ABC"); // 0
```

### 🔍 Summary Table

| Method                  | Purpose                 | Return Type | Case Sensitive? |
| ----------------------- | ----------------------- | ----------- | --------------- |
| `startsWith()`          | Check prefix            | `boolean`   | Yes             |
| `endsWith()`            | Check suffix            | `boolean`   | Yes             |
| `split()`               | Divide by delimiter     | `String[]`  | N/A             |
| `getChars()`            | Copy substring to array | `void`      | N/A             |
| `compareTo()`           | Lexical compare         | `int`       | Yes             |
| `compareToIgnoreCase()` | Lexical compare         | `int`       | No              |