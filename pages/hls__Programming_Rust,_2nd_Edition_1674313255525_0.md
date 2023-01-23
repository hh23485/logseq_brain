file:: [Programming_Rust,_2nd_Edition_1674313255525_0.pdf](../assets/Programming_Rust,_2nd_Edition_1674313255525_0.pdf)
file-path:: ../assets/Programming_Rust,_2nd_Edition_1674313255525_0.pdf

- [:span]
  ls-type:: annotation
  hl-page:: 17
  hl-color:: yellow
  id:: 63cbfebe-4697-429c-aa0a-2b9c042e2b61
  hl-type:: area
  hl-stamp:: 1674313404809
- The array a is only one element long, so using a[3] is, according to the C programming language standard, undefined behavior
  ls-type:: annotation
  hl-page:: 17
  hl-color:: yellow
  id:: 63cbfece-746a-41f3-b177-e5b074943c60
- Behavior, upon use of a nonportable or erroneous program construct or of erroneous data, for which this International Standard imposes no requirements
  ls-type:: annotation
  hl-page:: 17
  hl-color:: yellow
  id:: 63cbff28-fb20-47a4-a81c-5942a86c3fb7
- Undefined behavior doesn’t just have an unpredictable result: the standard explicitly permits the program to do anything at all
  ls-type:: annotation
  hl-page:: 17
  hl-color:: yellow
  id:: 63cbff30-fb9f-4be1-92ff-8184591cff22
- C and C++ have hundreds of rules for avoiding undefined behavior
  ls-type:: annotation
  hl-page:: 18
  hl-color:: yellow
  id:: 63cbff47-ba84-4a64-bdcc-5f2ba20a1449
- They’re mostly common sense: don’t access memory you shouldn’t, don’t let arithmetic operations overflow, don’t divide by zero, and so on
  ls-type:: annotation
  hl-page:: 18
  hl-color:: yellow
  id:: 63cbff4e-e3d2-4bc0-97ca-24fddbe543f8
- Indeed, the preceding program compiles without errors or warnings. The responsibility for avoiding undefined behavior falls entirely on you, the programmer.
  ls-type:: annotation
  hl-page:: 18
  hl-color:: yellow
  id:: 63cbff6f-fb28-4b17-88e0-dd2932bd5af1
- He found that nearly all programs do, including those from well-respected projects that hold their code to high standards. Assuming that you can avoid undefined behavior in C and C++ is like assuming you can win a game of chess simply because you know the rules
  ls-type:: annotation
  hl-page:: 18
  hl-color:: yellow
  id:: 63cbfff9-be9f-4f73-9cf8-48aaf16d572a
- The Rust language makes you a simple promise: if your program passes the compiler’s checks, it is free of undefined behavior
  ls-type:: annotation
  hl-page:: 20
  hl-color:: yellow
  id:: 63cc004e-c940-4ebb-9242-75d10e8ffdc3
- Dangling pointers, double-frees, and null pointer dereferences are all caught at compile time
  ls-type:: annotation
  hl-page:: 20
  hl-color:: yellow
  id:: 63cc0058-1075-47ea-8eee-a848a246fa94
- Array references are secured with a mix of compile-time and run-time checks
  ls-type:: annotation
  hl-page:: 20
  hl-color:: yellow
  id:: 63cc0068-dbc6-4eeb-8cbe-2e146cc957c3
- In our experience, being able to trust the language to catch more mistakes encourages us to try more ambitious projects. Modifying large, complex programs is less risky when you know that issues of memory management and pointer validity are taken care of
  ls-type:: annotation
  hl-page:: 20
  hl-color:: yellow
  id:: 63cc009f-a300-465b-8ed2-ebc335d8cd0e
- Concurrency is notoriously difficult to use correctly in C and C++
  ls-type:: annotation
  hl-page:: 21
  hl-color:: red
  id:: 63cc00ca-d929-4fd9-8efc-15108c02fcd0
  hl-stamp:: 1674313933732
- You can share data freely between threads, as long as it isn’t changing
  ls-type:: annotation
  hl-page:: 21
  hl-color:: yellow
  id:: 63cc0109-41f2-4b5b-b086-eca4288e7433
- Data that does change can only be accessed using synchronization primitives
  ls-type:: annotation
  hl-page:: 21
  hl-color:: yellow
  id:: 63cc0113-93b3-4605-acf7-ed1f6f541759
- traditional concurrency tools are available: mutexes, condition variables, channels, atomics, and so on. Rust simply checks that you’re using them properly
  ls-type:: annotation
  hl-page:: 21
  hl-color:: yellow
  id:: 63cc0123-b092-4e4d-8448-c67227901942
- The language is designed with efficient defaults and gives you the ability to control how memory gets used and how the processor’s attention is spent
  ls-type:: annotation
  hl-page:: 23
  hl-color:: yellow
  id:: 63cc01ce-cf06-4535-8db1-c5ca59c9fa05
- easy to use libraries published by others on Rust’s public package repository, the crates.io website
  ls-type:: annotation
  hl-page:: 23
  hl-color:: yellow
  id:: 63cc022c-89f0-4dbe-9e28-72d4e0e03d8b
- Rust’s traits and generics let you create libraries with flexible interfaces so that they can serve in many different contexts
  ls-type:: annotation
  hl-page:: 24
  hl-color:: yellow
  id:: 63cc024d-541a-4dd2-ab41-6d5bd661c084
- Chapter 2. A Tour of Rust
  ls-type:: annotation
  hl-page:: 25
  hl-color:: yellow
  id:: 63cc0289-aada-48c2-ab0e-5dfe15b62478
- a program that does a simple calculation on its command-line arguments, with unit tests
  ls-type:: annotation
  hl-page:: 25
  hl-color:: yellow
  id:: 63cc02a1-52f1-427c-89c0-f187716d6546
- use a third-party library to handle the details of HTTP and introduce string handling, closures, and error handling
  ls-type:: annotation
  hl-page:: 25
  hl-color:: yellow
  id:: 63cc04c6-b190-41ef-88a8-e0fb2bb93831
- plots a beautiful fractal, distributing the computation across multiple threads for speed
  ls-type:: annotation
  hl-page:: 25
  hl-color:: yellow
  id:: 63cc04cf-21b0-4815-954e-856491a0e29f
- a robust command-line tool that processes files using regular expressions
  ls-type:: annotation
  hl-page:: 26
  hl-color:: yellow
  id:: 63cc04d7-758c-490e-87c4-319f96569c0f
- The best way to install Rust is to use rustup . Go to https://rustup.rs and follow the instructions there
  ls-type:: annotation
  hl-page:: 26
  hl-color:: yellow
  id:: 63cc06e6-8739-4e7a-bfad-9645796eb77a
- when a new version of Rust is released, you’ll be able to upgrade with zero clicks by typing rustup update .
  ls-type:: annotation
  hl-page:: 27
  hl-color:: yellow
  id:: 63cc06ed-da6e-4c53-b0a5-bc4f79458b90
- [:span]
  ls-type:: annotation
  hl-page:: 27
  hl-color:: yellow
  id:: 63cc06f9-8993-46df-ab0b-dd68c2d8b43e
  hl-type:: area
  hl-stamp:: 1674315512237
- once you’ve completed the installation, you should have three new commands available at your command line:
  ls-type:: annotation
  hl-page:: 27
  hl-color:: yellow
  id:: 63cc06ff-1845-4fc5-b268-cea143e821ad
- cargo is Rust’s compilation manager, package manager, and general-purpose tool
  ls-type:: annotation
  hl-page:: 27
  hl-color:: yellow
  id:: 63cc0708-d192-4973-8477-7d8c6fd2c372
- rustc is the Rust compiler. Usually we let Cargo invoke the compiler for us, but sometimes it’s useful to run it directly.
  ls-type:: annotation
  hl-page:: 28
  hl-color:: yellow
  id:: 63cc070c-0f6e-45de-b7d7-5c47e076ede7
- rustdoc is the Rust documentation tool
  ls-type:: annotation
  hl-page:: 28
  hl-color:: yellow
  id:: 63cc070f-42d2-43f7-9d12-d2453dbb0306
- Cargo can create a new Rust package for us
  ls-type:: annotation
  hl-page:: 28
  hl-color:: yellow
  id:: 63cc0719-e0fb-4ec2-96a5-5a1c372c6a9d
- [:span]
  ls-type:: annotation
  hl-page:: 28
  hl-color:: yellow
  id:: 63cc071e-d82f-4dab-85a1-59955144b427
  hl-type:: area
  hl-stamp:: 1674315550024
- Cargo has created a file Cargo.toml to hold metadata for the package
  ls-type:: annotation
  hl-page:: 29
  hl-color:: yellow
  id:: 63cc092d-c4f5-4443-9082-5aa0679d0415
- You can tell Cargo to skip this step by passing `--vcs none` to cargo new on the command line.
  hl-page:: 30
  ls-type:: annotation
  id:: 63cc0959-92f3-431f-9186-c1e269345338
  hl-color:: yellow
- invoke the cargo run command from any directory in the package to build and run our program
  ls-type:: annotation
  hl-page:: 30
  hl-color:: yellow
  id:: 63cc0a09-c749-4a13-bf04-6ce3fc3a1784
- Cargo has invoked the Rust compiler, rustc , and then run the executable it produced.
  ls-type:: annotation
  hl-page:: 31
  hl-color:: yellow
  id:: 63cc0a98-5ee9-4c83-89dd-e5578f68cda2
- Cargo places the executable in the target subdirectory at the top of the package
  ls-type:: annotation
  hl-page:: 31
  hl-color:: yellow
  id:: 63cc0aab-2224-451b-ac1e-5e64850bef7f
- Cargo can clean up the generated files
  ls-type:: annotation
  hl-page:: 31
  hl-color:: yellow
  id:: 63cc0ac4-6095-4e68-b284-b23a25e5333b
- [:span]
  ls-type:: annotation
  hl-page:: 31
  hl-color:: yellow
  id:: 63cc0ade-5f2b-4e81-9cd0-d42dae81fad5
  hl-type:: area
  hl-stamp:: 1674316508973
- Four-space indentation is standard Rust style
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc11ce-a6f8-4ff0-9479-b856da9f5149
- i32 is a signed 32-bit integer
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc11d8-bfe7-4e57-897c-544136ba3f86
- u8 is an unsigned 8bit integer
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc11dd-bb6e-459b-a3aa-683a80ffc0c6
- used for “byte” values
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc11e1-7692-49ca-ab8a-0d40aabddd99
- The isize and usize types hold pointer-sized signed and unsigned integers
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 63cc1212-0fe8-4f3f-91ce-5bd579a33af4
  hl-stamp:: 1674318373242
- 32 bits long on 32-bit platforms, and 64 bits long on 64-bit platforms
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 63cc1221-1d77-4826-a8bd-92eb34d07ee7
  hl-stamp:: 1674318375636
- two floating-point types, f32 and f64
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc1243-aa94-4a9a-8f0b-deb6bd71cd41
- By default, once a variable is initialized, its value can’t be changed
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 63cc12bf-7242-49a5-81fa-ba4ea7502985
- but placing the mut keyword (pronounced “mute,” short for mutable) before the parameters n and m allows our function body to assign to them
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 63cc12c8-280a-4c3c-96da-a88e2bfcf870
- In practice, most variables don’t get assigned to
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc132d-ed0b-4cbd-bfc5-a866403502e5
- The function’s body starts with a call to the assert! macro
  ls-type:: annotation
  hl-page:: 33
  hl-color:: yellow
  id:: 63cc133a-f438-468d-85e6-4b25adca641a
- The ! character marks this as a macro invocation, not a function call
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 63cc1344-53a7-4168-a113-0488d0271afe
- it is not, terminates the program with a helpful message including the source location of the failing check; this kind of abrupt termination is called a panic
  ls-type:: annotation
  hl-page:: 34
  hl-color:: yellow
  id:: 63cc1395-bdc8-4f94-9562-dedd54d4efc1
- There is also a debug_assert! macro, whose assertions are skipped when the program is compiled for speed.
  ls-type:: annotation
  hl-page:: 34
  hl-color:: blue
  id:: 63cc13a8-6c89-4fa2-bbb2-978dccab8113
- nlike C and C++, Rust does not require parentheses around the conditional expressions, but it does require curly braces around the statements they control
  ls-type:: annotation
  hl-page:: 34
  hl-color:: blue
  id:: 63cc13d8-2d4b-440e-a63d-dd5c0e8c44f4
  hl-stamp:: 1674318931409
- If we wanted to spell out t ’s type, we could write:
  ls-type:: annotation
  hl-page:: 34
  hl-color:: yellow
  id:: 63cc1725-dc8b-4e8e-ba0b-dde052195b2e
- We don’t need to write out t ’s type, as long as Rust can infer it from how the variable is used
  ls-type:: annotation
  hl-page:: 34
  hl-color:: yellow
  id:: 63cc1730-b7e1-40e9-929a-1be5b9da0c70
- Rust has a return statement, but the gcd function doesn’t need one
  ls-type:: annotation
  hl-page:: 34
  hl-color:: yellow
  id:: 63cc1758-6f89-4693-b0f4-6b604b90c03e
- If a function body ends with an expression that is not followed by a semicolon, that’s the function’s return value
  ls-type:: annotation
  hl-page:: 34
  hl-color:: blue
  id:: 63cc1761-0e2e-49aa-945c-50d7ddf4e548
- return statements only for explicit early returns from the midst of a function.
  ls-type:: annotation
  hl-page:: 35
  hl-color:: yellow
  id:: 63cc177d-dd0a-4e51-8d2c-c08f628e109c
- Rust has simple support for testing built into the language
  ls-type:: annotation
  hl-page:: 35
  hl-color:: yellow
  id:: 63cc1787-2ba1-4723-8da9-4506ebb87a05
- [:span]
  ls-type:: annotation
  hl-page:: 35
  hl-color:: yellow
  id:: 63cc1793-40a4-447a-8b27-3a829e315307
  hl-type:: area
  hl-stamp:: 1674319761516
- define a function named test_gcd , which calls gcd and checks that it returns correct values
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17a2-a538-4f35-9c71-b4cca01afcd4
- #[test] atop the definition marks test_gcd as a test function, to be skipped in normal compilations
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17a9-8310-4414-bec4-f3ed735c7ab4
- included and called automatically if we run our program with the cargo test command
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17b0-52e9-42d2-a77d-456cc56e9880
- cargo test will automatically gather them up and run them all.
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17c4-daed-4154-aded-601ec6b12958
- The #[test] marker is an example of an attribute
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17cb-190a-4bfd-88cd-0519fe0ded0b
- ike attributes in C++ and C#, or annotations in Java
  ls-type:: annotation
  hl-page:: 36
  hl-color:: yellow
  id:: 63cc17d9-7860-42b3-bffa-4372446d196a
- [:span]
  ls-type:: annotation
  hl-page:: 37
  hl-color:: yellow
  id:: 63cc17fb-f173-4b67-8d7d-f97469ff91b1
  hl-type:: area
  hl-stamp:: 1674319866247
- Handling Command-Line Arguments
  ls-type:: annotation
  hl-page:: 37
  hl-color:: yellow
  id:: 63cc1813-fa89-464f-a9a3-38d671d319a2
- Rust Functions
  ls-type:: annotation
  hl-page:: 32
  hl-color:: yellow
  id:: 63cdfafb-b29a-4f3c-aeda-490f39cd6861
- a function that computes the greatest common divisor of two integers, using Euclid’s algorithm
  ls-type:: annotation
  hl-page:: 32
  hl-color:: yellow
  id:: 63cdfb08-342d-40c0-932c-6d2f361864be