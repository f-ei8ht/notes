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