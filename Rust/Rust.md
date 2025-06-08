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

# Memory management in Rust
when ever we run a program (C++, Rust, JS), it allocates and deallocates memory on the RAM. 
```js
function main() {
	runLoop();
}

function runLoop() {
	let x = [];
	for (let i = 0; i < 100000; i++) {
		x.push(1);
	}
	console.log(x);
}
```

as the `runLoop` function runs a new array is pushed to RAM, and eventually garbage collected

There are three popular ways of doing memory management 
1. Manually
2. Garbage Collection
3. Rust way

Garbage Collector: written by some smart people, no dangling pointers issues/memory issues, java and js.

manually: do manually allocate and deallocate memory by yourself can lead to dangling pointers, learning curve high, C, malloc calloc.

The rust way, ownership model for memory management, extremely safe to memory errors.


Memory management is a crucial aspect of programming in Rust designed to ensure safety and efficiency without the need for a garbage collector 

Not having a garbage collector is on of the key reasons rust is so fast

It achieves this using the mutability, heap and stack, ownership model, borrowing and references, lifetimes.

# Jargon 1: Mutability

immutable variables represent variables whose value cant be changed once assigned

```rust
fn main() {
	let x:i32 = 2;
	x = 2; // cannot mutate immutable variable x
	println!("{}",x);
}
```

by default all variables in rust are immutable just use `mut` keyword to make it mutable. Because immutable data is inherently thread safe because if no thread can alter the data, then no synchronization is needed when data is accessed concurrently.

knowing that certain data will not change allows the compiler to optimize code better.

```rust
fn main() {
	let mut x:i32 = 2;
	x = 4; // no error now
	println!("{}",x);
}
```

# Jargon 2: Stack vs Heaps

Rust has a clear rules about stack and heap data management
- Stack: fast allocation and de allocation. Rust uses the stack for most primitive data types and for data where the size is known at compile time (eg Numbers)
- Heap: used for data that can grow at runtime, such as vectors or strings.

What is stored on to the stack?
- Numbers: i32, i64, f64
- Booleans: true, false
- Fixed sized arrays

What is stored on to the heap?
- strings
- vectors

Examples
Hello world with numbers

we have something called stack frame one stack frame per function and every time goes inside that stack frame

```rust
fn main() {
	let num: i32 = 32;
	print_num(num);
}

fn print_num(num: i32) {
	print!("{}", num);
}
```

this will have to stack frame as two functions

in the end will get popped off 

```rust
fn main() {

    stack_fn();

    heap_fn();

    update_str();

}

  

fn stack_fn() {

    let a: i32 = 20;

    let b: i32 = 40;

    println!("Stack Function: Sum of {} + {} = {}",a,b,(a+b))

}

  

fn heap_fn() {

    let s1 = String::from("Hello");

    let s2 = String::from("World");

    let combine = format!("{} {}",s1,s2);

    println!("Heap Function: {combine}")

}

  

fn update_str() {

    let mut update = String::from("Saif Ali");

    println!("Initial String: {update}");

    for i in 0..100 {

        update.push_str(" Khan");

        println!("{} {} {:p}", update.capacity(), update.len(), update.as_str());

    }

}
```

Lets start from the first we have a `main` function first it will get loaded up in the stack lets say for now we have STACK FRAME with the main function 
Next we have `stack_fn()` function it will get in the stack with another STACK FRAME , it will do the things defined in it and then would probably get popped of.
next up we have `heap_fn()` function now it will get in the STACK FRAME and do the things will have the length (how many bytes are used) , capacity (bytes allocated to the heap) and the pointer of the string's value that points to data in the heap. Note that a third sttring will be created for the combine one.
Next up we will try to update a string and every thing same as the above but the things happen are the length and capacity change as the string kepts on updating increase also at some point the pointer address will also change meaning it will go to some other big space in the heap.

Out put

```bash
Stack Function: Sum of 20 + 40 = 60
Heap Function: Hello World
Initial String: Saif Ali
16 13 Pointer { addr: 0x6447d656cb10, metadata: 13 }
32 18 Pointer { addr: 0x6447d656cb70, metadata: 18 }
32 23 Pointer { addr: 0x6447d656cb70, metadata: 23 }
32 28 Pointer { addr: 0x6447d656cb70, metadata: 28 }
64 33 Pointer { addr: 0x6447d656cb70, metadata: 33 }
64 38 Pointer { addr: 0x6447d656cb70, metadata: 38 }
64 43 Pointer { addr: 0x6447d656cb70, metadata: 43 }
64 48 Pointer { addr: 0x6447d656cb70, metadata: 48 }
64 53 Pointer { addr: 0x6447d656cb70, metadata: 53 }
64 58 Pointer { addr: 0x6447d656cb70, metadata: 58 }
64 63 Pointer { addr: 0x6447d656cb70, metadata: 63 }
128 68 Pointer { addr: 0x6447d656cb70, metadata: 68 }
128 73 Pointer { addr: 0x6447d656cb70, metadata: 73 }
128 78 Pointer { addr: 0x6447d656cb70, metadata: 78 }
128 83 Pointer { addr: 0x6447d656cb70, metadata: 83 }
128 88 Pointer { addr: 0x6447d656cb70, metadata: 88 }
128 93 Pointer { addr: 0x6447d656cb70, metadata: 93 }
128 98 Pointer { addr: 0x6447d656cb70, metadata: 98 }
128 103 Pointer { addr: 0x6447d656cb70, metadata: 103 }
128 108 Pointer { addr: 0x6447d656cb70, metadata: 108 }
128 113 Pointer { addr: 0x6447d656cb70, metadata: 113 }
128 118 Pointer { addr: 0x6447d656cb70, metadata: 118 }
128 123 Pointer { addr: 0x6447d656cb70, metadata: 123 }
128 128 Pointer { addr: 0x6447d656cb70, metadata: 128 }
256 133 Pointer { addr: 0x6447d656cb70, metadata: 133 }
256 138 Pointer { addr: 0x6447d656cb70, metadata: 138 }
256 143 Pointer { addr: 0x6447d656cb70, metadata: 143 }
256 148 Pointer { addr: 0x6447d656cb70, metadata: 148 }
256 153 Pointer { addr: 0x6447d656cb70, metadata: 153 }
256 158 Pointer { addr: 0x6447d656cb70, metadata: 158 }
256 163 Pointer { addr: 0x6447d656cb70, metadata: 163 }
256 168 Pointer { addr: 0x6447d656cb70, metadata: 168 }
256 173 Pointer { addr: 0x6447d656cb70, metadata: 173 }
256 178 Pointer { addr: 0x6447d656cb70, metadata: 178 }
256 183 Pointer { addr: 0x6447d656cb70, metadata: 183 }
256 188 Pointer { addr: 0x6447d656cb70, metadata: 188 }
256 193 Pointer { addr: 0x6447d656cb70, metadata: 193 }
256 198 Pointer { addr: 0x6447d656cb70, metadata: 198 }
256 203 Pointer { addr: 0x6447d656cb70, metadata: 203 }
256 208 Pointer { addr: 0x6447d656cb70, metadata: 208 }
256 213 Pointer { addr: 0x6447d656cb70, metadata: 213 }
256 218 Pointer { addr: 0x6447d656cb70, metadata: 218 }
256 223 Pointer { addr: 0x6447d656cb70, metadata: 223 }
256 228 Pointer { addr: 0x6447d656cb70, metadata: 228 }
256 233 Pointer { addr: 0x6447d656cb70, metadata: 233 }
256 238 Pointer { addr: 0x6447d656cb70, metadata: 238 }
256 243 Pointer { addr: 0x6447d656cb70, metadata: 243 }
256 248 Pointer { addr: 0x6447d656cb70, metadata: 248 }
256 253 Pointer { addr: 0x6447d656cb70, metadata: 253 }
512 258 Pointer { addr: 0x6447d656cb70, metadata: 258 }
512 263 Pointer { addr: 0x6447d656cb70, metadata: 263 }
512 268 Pointer { addr: 0x6447d656cb70, metadata: 268 }
512 273 Pointer { addr: 0x6447d656cb70, metadata: 273 }
512 278 Pointer { addr: 0x6447d656cb70, metadata: 278 }
512 283 Pointer { addr: 0x6447d656cb70, metadata: 283 }
512 288 Pointer { addr: 0x6447d656cb70, metadata: 288 }
512 293 Pointer { addr: 0x6447d656cb70, metadata: 293 }
512 298 Pointer { addr: 0x6447d656cb70, metadata: 298 }
512 303 Pointer { addr: 0x6447d656cb70, metadata: 303 }
512 308 Pointer { addr: 0x6447d656cb70, metadata: 308 }
512 313 Pointer { addr: 0x6447d656cb70, metadata: 313 }
512 318 Pointer { addr: 0x6447d656cb70, metadata: 318 }
512 323 Pointer { addr: 0x6447d656cb70, metadata: 323 }
512 328 Pointer { addr: 0x6447d656cb70, metadata: 328 }
512 333 Pointer { addr: 0x6447d656cb70, metadata: 333 }
512 338 Pointer { addr: 0x6447d656cb70, metadata: 338 }
512 343 Pointer { addr: 0x6447d656cb70, metadata: 343 }
512 348 Pointer { addr: 0x6447d656cb70, metadata: 348 }
512 353 Pointer { addr: 0x6447d656cb70, metadata: 353 }
512 358 Pointer { addr: 0x6447d656cb70, metadata: 358 }
512 363 Pointer { addr: 0x6447d656cb70, metadata: 363 }
512 368 Pointer { addr: 0x6447d656cb70, metadata: 368 }
512 373 Pointer { addr: 0x6447d656cb70, metadata: 373 }
512 378 Pointer { addr: 0x6447d656cb70, metadata: 378 }
512 383 Pointer { addr: 0x6447d656cb70, metadata: 383 }
512 388 Pointer { addr: 0x6447d656cb70, metadata: 388 }
512 393 Pointer { addr: 0x6447d656cb70, metadata: 393 }
512 398 Pointer { addr: 0x6447d656cb70, metadata: 398 }
512 403 Pointer { addr: 0x6447d656cb70, metadata: 403 }
512 408 Pointer { addr: 0x6447d656cb70, metadata: 408 }
512 413 Pointer { addr: 0x6447d656cb70, metadata: 413 }
512 418 Pointer { addr: 0x6447d656cb70, metadata: 418 }
512 423 Pointer { addr: 0x6447d656cb70, metadata: 423 }
512 428 Pointer { addr: 0x6447d656cb70, metadata: 428 }
512 433 Pointer { addr: 0x6447d656cb70, metadata: 433 }
512 438 Pointer { addr: 0x6447d656cb70, metadata: 438 }
512 443 Pointer { addr: 0x6447d656cb70, metadata: 443 }
512 448 Pointer { addr: 0x6447d656cb70, metadata: 448 }
512 453 Pointer { addr: 0x6447d656cb70, metadata: 453 }
512 458 Pointer { addr: 0x6447d656cb70, metadata: 458 }
512 463 Pointer { addr: 0x6447d656cb70, metadata: 463 }
512 468 Pointer { addr: 0x6447d656cb70, metadata: 468 }
512 473 Pointer { addr: 0x6447d656cb70, metadata: 473 }
512 478 Pointer { addr: 0x6447d656cb70, metadata: 478 }
512 483 Pointer { addr: 0x6447d656cb70, metadata: 483 }
512 488 Pointer { addr: 0x6447d656cb70, metadata: 488 }
512 493 Pointer { addr: 0x6447d656cb70, metadata: 493 }
512 498 Pointer { addr: 0x6447d656cb70, metadata: 498 }
512 503 Pointer { addr: 0x6447d656cb70, metadata: 503 }
512 508 Pointer { addr: 0x6447d656cb70, metadata: 508 }
```

# Jargon 3: Ownership in Rust