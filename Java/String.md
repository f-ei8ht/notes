strings are nothing but group of characters 

in c/c++ a string is represented a an array of characters where the last character will be '\0'
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

## String methods