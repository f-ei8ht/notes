
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