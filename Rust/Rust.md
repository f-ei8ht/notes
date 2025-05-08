In rust if your program compiles, it probably works.
Rust is hard, and highly verbose to write code in rust compare to js or py
low-level, low-latency
c/c++, zig, rust
solana smart contract

You can not segfault if you do not have null. 
segfault = segmentation fault what is it? It is a type of program crash that happens when your code tries to access memory it should not, like reading or writing to a random place in memory or dereferencing (Dereferencing is a technique used to access or manipulate the value stored at a memory address pointed to by a pointer) a null . Think of it as your program touching memory it doesn't own — the operating system kills it.

Rust does not hides complexity from the developers it offers them the right tools to manage all the complexities.

what makes rust, rust => ownership, borrowing, references, lifetimes

## Why rust? Isn't Node.js enough?

js/py they do not have type safety and do not enforce types 

```js
let x = 1;
x = "obsidian"
console.log(x)
```

rust enforces types

```rust
fn main() {
	let x = 1;
	x = "obsidian"; // compilation error mismatched types
	// expected integer, fount `&str`
	println!("Hello");
}
```

now we have typescript and pylance pyright pydantic mypy

![](Pasted%20image%2020250506174927.png)

Rust is a systems languauge, intended to go low level

Builder a compiler
Building a browser
working close to os/kernel

Rust has a separate compilation setup that splits out an optimized binary and does a lot of static analysis at compile time.

concurrency as in java, go running multiple threads on a single machine
node js => single threaded

rust/java/go => threads
can run on multiple cores threads can also share resources need to do IPC (inter process communication) in node js

memory safe owners, borrowing, lifetimes

rustup rust tool chain 
cargo to manage project and crates just like npm

main.rs => index.js
cargo.toml => package.json

we get debug build because we compiling locally not in production when we use release flag `cargo build --release`
generally we use `cargo build and cargo run`

# Simple Variables in rust

you can use `let` keyword to define variables
you can assign the type of variable or it can be inferred as well

```rust
fn main() {
	let x: i32 = 4;
	println!("{}", x);
}
```

i => signed -ve/+Ve
u => unsigned positive only

```rust
fn main() {
	let x = 2;
	let y = 3;
	let z: u8 = 255;
	let z1: i8 = 127;
	let z2: i8 = -128;
	let z3 = 1.2;
	println!("{} {}", x, y);
	println!("{} {} {}", z, z1, z2);
	println!("{}", z3);
}
```

what can be the typescript code?

```ts
function main() {
  const x: number = 4;
  console.log(x);
}
main();
```

what is there is a overflow?

```rust
fn main() {
	let mut x: i8 = 10;
	for _i in 0..1000 {
		x = x + 100;
	}
	print!("{}", x);
}
```

it will build meaning it will compile but not run 
`thread 'main' panicked at src/main.rs:4:13:attempt to add with overflow`

boolean are normal just like `true` and `false` in any other language.

```rust
fn main() {
	let is_male = false;
	let is_above18 = true;
	if is_male {
		println!("You are not Male");
	} else if is_male && is_above18 {
		print!("You are a Male and you can vote");
	} else {
		print!("You are not male and you cannot vote");
	}
}
```

Strings are fairly complicated in rust, we have

```rust
fn main() {
	let mut s = String::from("Hello");
	println!("{}", s);
	let s1: &'static str = "saif";
	print!("{}", s1)
}
```

you can use String::from which is mutable if using mut but not the string slice as it is borrowed &str most probably used with functions, parameters but the static str is related to lifetimes and should be use with literals and constants.

In strings you cannnot access the index like in js/ts

```js
function main() {
	let s = "saif";
	console.log(s[0]);
}
main()
```

no rust does not allows that it says may be there can be something or me be not 

```js
// if we try to access some very big index
console.log(s[1000]); // undefined 
```

js does not cares it just prints out undefined

rust compiler will not allow anything like this 
we can do pattern matching which will be discussed later on for the time being we can use `unwrap` which tells the compiler its okay there is something i know you have to be sure about.

**`unwrap`** generally refers to a method or function that **extracts the value inside a container or wrapper**, assuming the value is present and valid.

```rust
let c = s.chars().nth(2);
println!("{}", c.unwrap());
```

if you try to access a index where nothing is present you will get something like this

```bash
thread 'main' panicked at string.rs:9:22:
called `Option::unwrap()` on a `None` value
```


# Conditionals in rust

if else are pretty straightforward in rust just like any other language 

```rust
fn main() {
	let x = 2;
	let is_even = is_even(x);
	if is_even {
		println!("{} This is even number", x);
	} else {
		println!("{} This is odd number", x);
	}
}
fn is_even(n: i32) -> bool {
	return n % 2 == 0;
}
```

lets see how for loops work in rust 
`for i in 0..10` it will iterate till 10 - 1 = 9
one less

how to get the first word from the string we will use for loop to iterate over the string using chars() then until no space found we will push the characters one by one to a new string 

```rust
fn main() {
	let sentence = String::from("my name is saif");
	let first_word = get_first_word(sentence);

	for i in 0..1000 {
		let i: i64 = i as i64;
		println("hello world: {}", i);
	}
	
	println!("{}", first_word);
}

fn get_first_word(sentence: String) -> String {
	let mut word = String::from("");
	for char in sentence.chars() {
		word.push_str(char.to_string().as_str());
		if char == ' ' {
			break;
		}
	}
return word;
}
```

#todo
rust does not allow to change i in the loop syntax i think so need to confirm first but you can cast it to be i64 like i did and there must be some other ways as well. need to find

# Functions in rust

pretty straight forward

```rust
fn main() {
	let x = add_num(2,3);
	println!("{}",x);
}

fn add_num(a: i32, b: i32) -> i32 {
	return a + b;
}
```
 new thing to learn only is that `-> i32` return type of the function there.