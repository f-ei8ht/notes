# Syntax

In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), the **syntax** of a [computer language](https://en.wikipedia.org/wiki/Computer_language "Computer language") is the rules that define the combinations of symbols that are considered to be correctly structured [statements](https://en.wikipedia.org/wiki/Statement_\(computer_science\) "Statement (computer science)") or [expressions](https://en.wikipedia.org/wiki/Expression_\(computer_science\) "Expression (computer science)") in that language. This applies both to [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"), where the document represents [source code](https://en.wikipedia.org/wiki/Source_code "Source code"), and to [markup languages](https://en.wikipedia.org/wiki/Markup_language "Markup language"), where the document represents data. The syntax of a language defines its surface form.

--- 

# Expression

In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), an **expression** is a [syntactic](https://en.wikipedia.org/wiki/Syntax_\(programming_languages\) "Syntax (programming languages)") entity in a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") that may be evaluated to determine its [value](https://en.wikipedia.org/wiki/Value_\(computer_science\) "Value (computer science)").[[1]](https://en.wikipedia.org/wiki/Expression_\(computer_science\)#cite_note-1) It is a combination of one or more [constants](https://en.wikipedia.org/wiki/Constant_\(programming\) "Constant (programming)"), [variables](https://en.wikipedia.org/wiki/Variable_\(programming\) "Variable (programming)"), [functions](https://en.wikipedia.org/wiki/Function_\(programming\) "Function (programming)"), and [operators](https://en.wikipedia.org/wiki/Operator_\(programming\) "Operator (programming)") that the programming language interprets (according to its particular [rules of precedence](https://en.wikipedia.org/wiki/Order_of_operations "Order of operations") and of [association](https://en.wikipedia.org/wiki/Associative_property "Associative property")) and computes to produce ("to return", in a [stateful](https://en.wikipedia.org/wiki/State_\(computer_science\) "State (computer science)") environment) another value. This process, for [mathematical expressions](https://en.wikipedia.org/wiki/Mathematical_expression "Mathematical expression"), is called _evaluation_. In simple settings, the [resulting value](https://en.wikipedia.org/wiki/Return_type "Return type") is usually one of various [primitive types](https://en.wikipedia.org/wiki/Primitive_data_type "Primitive data type"), such as [string](https://en.wikipedia.org/wiki/String_\(computer_science\) "String (computer science)"), [boolean](https://en.wikipedia.org/wiki/Boolean_expression "Boolean expression"), or numerical (such as [integer](https://en.wikipedia.org/wiki/Integer_\(computer_science\) "Integer (computer science)"), [floating-point](https://en.wikipedia.org/wiki/Floating-point_number "Floating-point number"), or [complex](https://en.wikipedia.org/wiki/Complex_data_type "Complex data type")).

Expressions are often contrasted with [statements](https://en.wikipedia.org/wiki/Statement_\(computer_science\) "Statement (computer science)")—[syntactic](https://en.wikipedia.org/wiki/Syntactic "Syntactic") entities that have no value (an instruction).

---

# Statements

In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **statement** is a [syntactic](https://en.wikipedia.org/wiki/Syntax_\(programming_languages\) "Syntax (programming languages)") unit of an [imperative programming language](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") that expresses some action to be carried out.[[1]](https://en.wikipedia.org/wiki/Statement_\(computer_science\)#cite_note-1) A [program](https://en.wikipedia.org/wiki/Computer_program "Computer program") written in such a language is formed by a sequence of one or more statements. A statement may have internal components (e.g. [expressions](https://en.wikipedia.org/wiki/Expression_\(computer_science\) "Expression (computer science)")).

Many programming languages (e.g. [Ada](https://en.wikipedia.org/wiki/Ada_\(programming_language\) "Ada (programming language)"), [Algol 60](https://en.wikipedia.org/wiki/Algol_60 "Algol 60"), [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"), [Java](https://en.wikipedia.org/wiki/Java_\(programming_language\) "Java (programming language)"), [Pascal](https://en.wikipedia.org/wiki/Pascal_\(programming_language\) "Pascal (programming language)")) make a distinction between statements and [definitions/declarations](https://en.wikipedia.org/wiki/Declaration_\(computer_programming\) "Declaration (computer programming)"). A definition or declaration specifies the data on which a program is to operate, while a statement specifies the actions to be taken with that data.

Statements which cannot contain other statements are _simple_; those which can contain other statements are _compound_.[[2]](https://en.wikipedia.org/wiki/Statement_\(computer_science\)#cite_note-ALGOL60-2)

The appearance of a statement (and indeed a program) is determined by its [syntax](https://en.wikipedia.org/wiki/Syntax_\(programming_languages\) "Syntax (programming languages)") or grammar. The meaning of a statement is determined by its [semantics](https://en.wikipedia.org/wiki/Semantics_\(computer_science\) "Semantics (computer science)").

---

# Variables

A variable is a symbolic name for (or reference to) information. The variable's name **represents** what information the variable contains. They are called **variables** because the represented information can change but the **operations** on the variable remain the same. In general, a program should be written with "Symbolic" notation, such that a statement is **always true** symbolically.

--- 

# Token

A _lexical token_ is a [string](https://en.wikipedia.org/wiki/String_\(computer_science\) "String (computer science)") with an assigned and thus identified meaning, in contrast to the probabilistic token used in [large language models](https://en.wikipedia.org/wiki/Large_language_model "Large language model"). A lexical token consists of a _token name_ and an optional _token value_. The token name is a category of a rule-based lexical unit.[[2]](https://en.wikipedia.org/wiki/Lexical_analysis#cite_note-auto-2)

| Token Name | Explanation | Sample Token Values |
|------------|------------|---------------------|
| [Identifier](https://en.wikipedia.org/wiki/Identifier_\(computer_languages\) "Identifier (computer languages)") | Names assigned by the programmer. | `x`, `color`, `UP` |
| [Keyword](https://en.wikipedia.org/wiki/Reserved_word "Reserved word") | Reserved words of the language. | `if`, `while`, `return` |
| [Separator/Punctuator](https://en.wikipedia.org/wiki/Delimiter "Delimiter") | Punctuation characters and paired delimiters. | `}`, `(`, `;` |
| [Operator](https://en.wikipedia.org/wiki/Operator_\(computer_programming\) "Operator (computer programming)") | Symbols that operate on arguments and produce results. | `+`, `<`, `=` |
| [Literal](https://en.wikipedia.org/wiki/Literal_\(computer_programming\) "Literal (computer programming)") | Numeric, logical, textual, and reference literals. | `true`, `6.02e23`, `"music"` |
| [Comment](https://en.wikipedia.org/wiki/Comment_\(computer_programming\) "Comment (computer programming)") | Line or block comments. Usually discarded. | `/* Retrieves user data */`, `// must be negative` |
| [Whitespace](https://en.wikipedia.org/wiki/Whitespace_character "Whitespace character") | Groups of non-printable characters. Usually discarded. | – |

---

# Naming Conventions

https://dev.to/mutu/variable-naming-techniques-24hn
https://www.freecodecamp.org/news/how-to-write-better-variable-names

---

# Datatypes

In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science") and [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **data type** (or simply **type**) is a collection or grouping of [data values](https://en.wikipedia.org/wiki/Value_\(computer_science\) "Value (computer science)"), usually specified by a set of possible values, a set of allowed operations on these values, and/or a representation of these values as machine types.[[1]](https://en.wikipedia.org/wiki/Data_type#cite_note-FOOTNOTEParnasShoreWeiss1976-1) A data type specification in a program constrains the possible values that an [expression](https://en.wikipedia.org/wiki/Expression_\(computer_science\) "Expression (computer science)"), such as a variable or a function call, might take. On literal data, it tells the [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") or [interpreter](https://en.wikipedia.org/wiki/Interpreter_\(computing\) "Interpreter (computing)") how the programmer intends to use the data. Most programming languages support basic data types of [integer](https://en.wikipedia.org/wiki/Integer_\(computer_science\) "Integer (computer science)") numbers (of varying sizes), [floating-point](https://en.wikipedia.org/wiki/Floating_point "Floating point") numbers (which approximate [real numbers](https://en.wikipedia.org/wiki/Real_number "Real number")), [characters](https://en.wikipedia.org/wiki/Character_\(computing\) "Character (computing)") and [Booleans](https://en.wikipedia.org/wiki/Boolean_data_type "Boolean data type").[[2]](https://en.wikipedia.org/wiki/Data_type#cite_note-2)[[3]](https://en.wikipedia.org/wiki/Data_type#cite_note-3)

--- 

# Parameters vs. Arguments

Parameters are the names used for inputs when _defining_ a function. Arguments are the values of the inputs supplied when a function is _called_.

To reiterate, **arguments are the actual values** that go into the function, such as `42.0`, `"the dark knight"`, or `True`. **Parameters are the names** we use in the function definition to refer to those values, which at the time of writing the function, can be whatever we like.

---

# Relative vs Absolute url

Absolute url are the full path to a resource with the protocols (http/https)

Relative url within a web page with no protocol

---

# I got to know one in objects syntax in java

lets say we have an instance method and we create an instance of an class then we can use the reference variable with the methods name like this if we want to call it multiple times

```java
obj.methodName().methodName().methodName()
```

I found this so dope man this is known as `method-chaining`.

---

Bootstrapped languages that are implemented in their own language