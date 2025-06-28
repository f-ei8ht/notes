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