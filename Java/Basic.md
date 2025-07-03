## History of Java ☕

- `James Gosling` , `Sun Microsystems`
- first release 1995
- previously called as `oak`
- named after java islands because of their coffee beans

## Features

- Java is *backward compatible*
- Java is *robust*
- Java is *oops* based
- Java is *multi threaded*
- Java is *distributed*
- **WORA**, platform independent (Write once run anywhere)
- Java uses compiler and interpreter both (jvm -> interpret or jit compiled)

## Buzzwords

1. `Bytecode` : a verified code that is not human readable made by converting source code using java compiler which will then convert to machine code by jvm.
2. `Robust` : means strong, hence java is robust strong exception handling, type checking, strong memory management.
3. `Multi-threaded` : means the ability to execuate a lot of threads concurrently of CPU.
4. `Distributed` : good in communicating with network protocols.
5. `JIT` : just in time compiler

## How does java source code gets converted to machine code?

Firstly the programmers writes the code on any text editor or IDE,
then java compiler compiles the code to byte code which is intermediate code
and is not human readable then the `JVM` converts the byte code to
machine code 0's and 1's.

```mermaid
flowchart LR
	A["Source Code
	(.java)"]
	-- Compiler
	(javac) --- B["Bytecode
	(.class)"] -- JVM
	(java) --- C["OS
	(Native Code)"] .- D["Windows JVM"] & E["Linux JVM"] & F["MacOS JVM"]
```

## Files Extensions

`.java [sourcecode]` and `.class [bytecode]`
  * [ ] 
## JDK VS JVM VS JRE

```mermaid
graph TD
	subgraph JDK["Java Development Kit"]
		A[Java Development
		Tools. Like javac,
		jdoc, java etc.]
		subgraph JRE["JRE"]
			B["JVM
			(Java Virtual Machine)"]
			C[Set of java Libraries.
			Like java.lang, java.util,etc.]
		style A fill:#fff,color:#000,stroke:#000000
		style JRE fill:#fff,color:#000,stroke:#000000
		style B fill:#b7e892,color:#000,stroke:#000000,stroke-dasharray:5,5
		style C fill:#ff9090,color:#000,stroke:#000000,stroke-dasharray:5,5
		end
		style JDK fill:#dff2ff,color:#000,width:670px,height:360px
    end
```

`JDK` : it includes JRE, interpreter/loader (java), javac javadoc, and other tools needed for Java Development. Essentially, JDK is superset of JRE.
`JRE` : it is a part of JDK, but can be downloaded seprately. Provides libraries, the JVM, and other components to run application.
`JVM` : its a part of JRE and is responsible for executing the bytecode. "WORA" capability. Not platform independent.

## Print Statements

- `print("one")` : prints is one line, uses no new line
- `println("two")` : first prints then goes to a new line
- `println()` : will print a new line

For Example =>

```java
public class PrintStatement {
	public static void main(String[] args) {
		System.out.print("one");
		System.out.println();
		System.out.print("two");
		System.out.println("three");
		System.out.print("four");
	}
}
```

```bash
$ output
one
twothree
four
```

## Importance of the main method

- *Enrty point* : it's the entry point of a Java program, when the execution starts, JVM looks for main method.
- *public* and *static* : main method must be accessible to jvm without needing to instantiate the class.
- fix signature => public static void main(String[] args)

## What are variables?

- Variables are like containers used for storing data values.

```mermaid
graph LR
	A["int a = 5;"] .-> id1([5 => value of variable a]) & id2([a => name      of the variable]) & id3([int => datatype])
```

- You can see here a variable `int a` has value `5`;
- It has integer datatype (will discuss about this later)
- For now integer has 4 bytes (32 bits) of size in java, so JVM will allocate 4 bytes for the variable a onto stack.
- Variable name does not gets stored onto the stack.
- There is a concept of address on the memory.

## Data Types

![Data Types](datatypes.png "Data Types")

  In the table above you can see different different types of datatypes that are used in java.

```mermaid
flowchart TB
	id1(Java DataTypes) ---> A["Primitive Data Types"] & B["Non-Primitive     Data Types"]
	A .-> C["Boolean"] & D["Numeric"]
	B .-> E["strings"] & F["arrays"] & G["objects"]
	C .-> H["boolean"]
	D .-> I["Character"] & J["Integral"]
	I .-> K["char"]
	J .-> L["Integer"] & M["Floating Point"]
	L .-> N["byte"] & O["short"] & P["int"] & Q["long"]
	M .-> R["float"] & S["double"]
```

In the above mermaid diagram you can have an overview of `Primitive` and `Non-Primitive` data types.

## Naming Conventions

### camelCase

- Start with a lowercase letter. Capitalize the first letter of each subsequent word.
- Example => `myVariableName`

### snake_case

- Start with an lowercase letter. Separate words with underscore.
- Example: `my_variable_name`

### kebab-case

- All lowercase letters. Separate words with hypens.
- Example : `my-variable-name`

Keep a good and short name, choose names that are descriptive but not too long. It should be make the variable's purpose understandable.

## Identifier Rules in Java

1. The only allowed characters for identifiers are all alphanumeric characters([A-Z], [a-z], [0-9]), '$' (dollar sign) and '_' (underscore).
2. Can't use keywords or reserve words.
3. Identifiers should not start with digits([0-9]).
4. Java identifiers are case-sensitive.
5. There is no limit on the length of the identifier but it is advisable to use an optimum length of 4 - 15 letters only.
6. Example =>

![Identifers Valid/Invalid](identifiers_valid_invalid.png "Identifiers Valid/Invalid")
## Literals

- Integer literals => 10, 5, -8 etc ..
- Floating-point literals => 1.2, 0.25, -1.999, etc...
- Boolean literals => true, false
- Character literals => 'a', 'A', 'N', 'q', etc...
- String literals => "hi", "hello", "what's up?"
- Values that the varibales hold are called literals.

## Keywords

Here is a list of keywords in the Java programming language. You cannot use any of the following as identifiers in your programs. The keywords const and goto are reserved, even though they are not currently used. true, false, and null might seem like keywords, but they are actually literals; you cannot use them as identifiers in your programs.

| abstract  | continue | for        | new        | switch       |
| --------- | -------- | ---------- | ---------- | ------------ |
| assert*** | default  | goto*      | package    | synchronized |
| boolean   | do       | if         | private    | this         |
| break     | double   | implements | protected  | throw        |
| byte      | else     | import     | public     | throws       |
| case      | enum**** | instanceof | return     | transient    |
| catch     | extends  | int        | short      | try          |
| char      | final    | interface  | static     | void         |
| class     | finally  | long       | strictfp** | volatile     |
| const*    | float    | native     | super      | while        |

\* not used
\*\* added in 1.2
\*\*\* added in 1.4
\*\*\*\* added in 5.0

Go to this md for more information => [Keywords.md](Keywords.md)

## Escape Sequence

| Escape Sequence | Description                                                                                  |
| --------------- | -------------------------------------------------------------------------------------------- |
| `\t`            | Inserts a horizontal tab space in the string, typically equivalent to a few spaces.          |
| `\'`            | Inserts a single quote character in the text at this point.                                  |
| `\"`            | Includes a double quote character within a string enclosed by double quotes.                 |
| `\r`            | Inserts a carriage return in the text at this point.                                         |
| `\\`            | Represents a single backslash in the string.                                                 |
| `\n`            | Inserts a new line in the string, causing subsequent characters to be printed on a new line. |
| `\f`            | Inserts a form feed in the text at this point.                                               |
| `\b`            | Represents the backspace control character, moving the cursor one position backwards.        |

## User Input

- Scanner class
- Buffer reader
- Command line arguments
- Console class
- File reader
- Object Input Stream
- Properties
- Data Input Stream

  
Scanner class =>

| Method            |
| ----------------- |
| next( )           |
| nextLine( )       |
| nextInt( )        |
| nextDouble( )     |
| nextFloat( )      |
| nextLong( )       |
| nextByte( )       |
| nextShort( )      |
| nextBigInteger( ) |
| nextBigDecimal( ) |
| nextBoolean( )    |

## Type Conversion

Automatic Type Conversion
(Widening - Implicit - coercion)

```mermaid

flowchart LR

A["byte"] --> B["short"] --> C["int"] --> D["long"] --> E["float"] --> F["double"]

```

Narrowing
(explicit - casting)

```mermaid

flowchart RL

A["byte"] --> B["short"] --> C["int"] --> D["long"] --> E["float"] --> F["double"]

```

Some Examples =>

```java
// implicit
long big = 45;
float dec = 4;
double d = 3.4f;

// explicit
float eDec = (float) 3.4;
long eBig = (long) 3.4;
int eInt = (int) 3.4;
```

## Assignment operators

Assigns the right hand operand's value to the left hand operand

```java
//example
int a = 5;
int b = a;
```

- += => Addition and assign , x += 4; x = x + 4
- -= => Subtraction and assign , x -= 4; x = x - 4
- \*= => Multiplication and assign , x *= 4; x = x * 4
- /= =>  Division and assign , x /= 4; x = x / 4
- %= => Modulo and assign , x %= 4; x = x % 4

They are also called short hand operators. 👆

## Unary Operators

- - => unary minus , x = -y
- + => probably redundant
- ++ -- => post and pre
- ! => not for reversing boolean 

## Arithmetic Operators

| Operators | Meaning                                               | Example |
| --------- | ----------------------------------------------------- | ------- |
| +         | Addition                                              | x + y   |
| -         | Substraction                                          | x - y   |
| *         | Multiplication                                        | x * y   |
| /         | Division                                              | x / y   |
| %         | Modulus operator to get remainder in integer division | x % y   |

## Order of Operation

*`BODMAS OR PEMDAS`*


## If-else

- use if ( ) { } to check a condition
- if => execute block if condition is true, skips if false.
- else => execute a block when the condition is false.
- curly braces => can be omitted for single statements, but not recommended.
- if-else Ladder => multiple if and else if blocks, only one executes.
- Use variables: can store conditions in variables for use in if statements.

## Relational Operators

- Equality 
	- == checks value equality

- Inequality 
	- != checks value inequality

- Relational 
	- > Greater than
	- < Less than
	- <= Less than or equal to
	- >= Greater than or equal to

## Logical Operators

Types: && (AND), || (OR), ! (NOT)
- AND (&&): All conditions must be true for the result to be true.
- OR (||): Only one condition must be true for the result to be true.
- NOT (!): Inverts the Boolean value of a condition.

## Operator Precedence

![Operator Precedence](operator-precedence.jpeg)

- operator precedence - Determine the evaluation order according to their priority
- highest to lowest in the above image
- associativity - order of operation for same precedence of operators

## Bitwise operator

Bitwise AND (&) : performed on two integers
Bitwise OR (|): performed on two integers
Bitwise Xor (^): A'.B + A.B' performed on two integers
Bitwise complement (~): 0 to 1 and 1 to 0
Bitwise Left shift (<<): Shift the left operand bits to left
Bitwise Right shift (>>): shift the left operand bits to right

| 0   | 0000 |
| --- | ---- |
| 1   | 0001 |
| 2   | 0010 |
| 3   | 0011 |
| 4   | 0100 |
| 5   | 0101 |
| 6   | 0110 |
| 7   | 0111 |
| 8   | 1000 |
| 9   | 1001 |
| 10  | 1010 |
| 11  | 1011 |
| 12  | 1100 |
| 13  | 1101 |
| 14  | 1110 |
| 15  | 1111 |

## Comments

Single line: // 
multi line: `/* */`
java doc: `/** */`

```java
/**
*@param args
*
*/
```

## While loop

always include a update to avoid infinte looping
while condition true used for non standard conditions

```java
int n = 1; // initilization
while(n > 0) { // condition
	// body of loop
	n--; // updation
}
```
- initialization
- condition
- updation

## Functions/Methods

- #note most important => in java there are methods because functions are always written inside class, hence the functions written inside class are methods.
- DRY principle: Do not repeat yourself
- reusable block of code
- organises code
- camelCase naming 
- function always go in stack because a function below will wait for the function over it to get finished first
```java
public static int sum(int a, int b) { // a and b are parameters give to the fn
	int c = a + b; 
	return c;
}

public static void main(String[] args) {
	int result = sum(3,4); // 3 and 4 are arguments given to the fn sum
	System.out.println(result);
}

```

## Return Statement

- Used to return a value from the function.

## Pass by value

```java
public static int sum(int a, int b) { // a and b are parameters give to the fn
	int c = a + b; 
	return c;
}

public static void main(String[] args) {
	int num1 = 10, num2 = 20; 
	int result = sum(num1, num2); // 3 and 4 are arguments given to the fn sum
	System.out.println(result);
	// java creates a copy does not makes any reference here
}
```


objects reference are passed but it is also pass by value because a copy of reference is passed. 

## Ternary Operator

syntax 

result = num1 > num2 ? true : false;
only one thing to keep in mind is that the type should be same

## Switch case

```java
swtich(choice) {
	case 1:
		// expression
		break;
	default: 
		// expression
}
```

accepts the primitives and enum as well long double float from java 14 types should be same

## Do While Loop

```java
int count = 1;
do {
    System.out.println("Count is: " + count);
    count++;
} while (count <= 5);

```

it will execute once one iteration will be made

## For Loop
```java
for(int i = 1; i < 5; i++) {
	System.out.println("Count is: " + i);
}
```

## For each loop 

we generally use for loop if we want to read through arrays or a collection of data basically what I learned

```java
package Challenge10;

  

public class Loop {

    public static void main(String[] args) {

        // for (int i = 1;;) {

        // if (i > 5) {

        // break;

        // }

        // System.out.println(i);

        // i++;

        // }

        String[] names = { "SAIF", "SAAD", "Shoaib", "YUSUF" };

  

        for (String name : names) {

            if (name.equals("SAIF"))

                name = "no"; // copy of the array not original

            System.out.println(name);

        }

        System.out.println(names[0]);

    }

}
```

### **Labeled loops** 🔁 (rare use case)

Used with `break` or `continue` to jump to specific outer loops.

```java
package Challenge10;

  

public class Label {

    public static void main(String[] args) {

        outerLoop: // this is a label

        for (int i = 0; i < 3; i++) {

            for (int j = 0; j < 3; j++) {

                if (j == 2)

                    break outerLoop;

                System.out.println("i=" + i + ", j=" + j);

            }

        }

  

    }

}
```
**Meaning:**  
`break outerLoop;` will break **out of the labeled outer loop**, not just the inner loop.

## Break statement
we can use label to break out of some loop like it can be inner or outer as well but the break only work for a certain scope only 
```java
package BreakandContinue;

  

public class Break {

    public static void main(String[] args) {

        outer: for (int i = 0; i < 10; i++) {

            for (int j = 0; j < 1000; j++) {

                if (j == 101)

                    break outer;

                System.out.println(j);

            }

        }

    }

}
```

I we remove outer here then the inner loop will exit if we gonna use a label then the outer loop will be exited break is also used with switch 

## Continue statement
```java
package BreakandContinue;

  

public class Continue {

    public static void main(String[] args) {

        outer: for (int i = 0; i < 10; i++) {

            for (int j = 0; j < 5; j++) {

                if (j == 2)

                    continue outer;

                System.out.print(j);

            }

        }

    }

}
```

continue just skips the condition that is met true like here j == 2 then the label will take the control to the outer loop.

in while loop during the continue to avoid infinite loop we have to update the while loop above the continue statement.

## **toString()** method

provides a string representation of a string object.
```java
package toString;

  

import java.util.Arrays;

  

public class ToString {

    public static void main(String[] args) {

        String s = "saif";

        System.out.println(s.toString()); // even if we not use toString it will be applied by the jvm.

        int[] a = { 1, 2, 3 };

        System.out.println(Arrays.toString(a)); // internally working with append and string builders will return the

                                                // array with square brackets and values seprated by commas

    }

}
```

```cmd
[1,2,3]
```

and from here we can confirm that it is inherited from the object class

by default results classname@hashcode

`[I@372f7a8d`

if we try to print a it will return this here I means integer and the `[` means its and array the @ is just a separator and the hash value at the end is generated by the hashcode method
what happens is something like this we can say that this hashcode is generated from the identity of object that is maintained or known to the jvm.

```java
public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

same objects compared using equals() will have the same hash but not necessary the different objects cannot have same hash, they can have same hash this is called collision and modern jvm's work in a way to avoid this. 
hashcode is for the benefit of hash tables.

## final keyword

we all know what it does it makes things constant and helps the compiler optimize things during compilation only.