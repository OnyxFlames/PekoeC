# Language
## Description
Pekoe is a C-like language with a twist, enabling safer memory operations, while sacrificing little performance for the overhead.

## Target Language
Pekoe will target C99, and use a 3rd-party C compiler to compile the output, taking advantage of the optimizations from the given compiler.

## Keywords
Keywords are words reserved by the language and cannot be used as identifiers.

### General
* as
* cast
* struct
* class
* sizeof
* addrof
* static
* const
* enum
* extern

### Loop keywords
Pekoe supports 4 different types of loops
* for
* while
* do-while
* until

### Control Flow
These keywords are used to affect how the program flows
* switch
* case
* break
* default
* return
* if
* else
* goto

## Comments
Pekoe will support C99 comments, as well as multi-line comments
```c
    // C99 comment
    /* 
        multi-
        lined
        comment
    */
```

## Primitive types
* i8 and u8
* i16 and u16
* i32 and u32
* i64 and u64
* f32 and f64

and
* void


Array variants are also supported, therefore C-strings will be implicitly allowed, but will be replaced with other language constructs.
Since array variants are supported, pointers to types are inherently supported as well.

### Array Type Declaration
Array declarations deviate from C and follow C#'s method of including the [] with the type signature.
See [variable declaration](#VariableDeclaration) for an example.

### Functions as First-Class Members
Unlike C, Pekoe will treat functions as first class members, allowing them to be passed as arguments to functions or be return types from functions.

## Identifier
An identifier is any word beginning with [_a-zA-Z], followed by [_a-zA-Z0-9]
Identifiers can refer to variables, functions, or struct/class instances.

## <a name="VariableDeclaration"></a>Variable Declaration
Declaring a variable in Pekoe is simple.

Example: a 32bit integer named foo, set to 100
```
foo : i32 = 100;
```

Example: a 32bit float without a default value, named bar
```
bar : f32;
```
Example: an array with the length of 8 of 16bit integers
```
foobar : i16[8];
```
Example: a pointer to an i32, whether its a single i32 or a undetermined array
```
bast : i32*;
```

Declaring a class in Pekoe is similar in style.

Example: A barebones string class
```
string : class
{
    size : i32;
    capacity : i32;
    data : u8*;
};
```
Member functions will be covered when normal function declarations are covered.

## <a name="FunctionDeclaration"></a>Function Declaration
Functions are defined similarly to variables, to keep in line with the fact that they can be treated as first class members in *most* cases.
```
add : (x : i32, y : i32) -> i32;
```
Will define a function called *add*, which takes two i32's (namely *x* and *y*), and returns one i32

Although a little complicated, a function can return another function
```
adder : (x : i32) -> (y : i32) -> i32
{
    return (y : i32) -> i32
    {
        return x + y;
    };
}
```
The above code will return a function that takes *y* and adds *x* to *y*, returning the result.

## Including other files
To deviate from the archaic style of including files that is C, Pekoe uses a simpler format:
the *using* keyword.

Example: *Including the IO and string formatting libraries.*
```c
using Std.IO.write;
using Std.String.format;

write("Hello, World!");
write(format("Goodbye, {}\n", "World!"));
```

Unlike C, each files inclusion will be logged internally, preventing the need of a system like header guards.

The Std namespace is reserved for Pekoe Standard Library files, and limits the search to the std/ folder next to the compiler

## Interacting with C code
Pekoe can utilize C code by labelling a block as
```c
extern "C" function_name();
```
This function will remain unmangled, and be called directly in the C output.
This allows Pekoe to utilize C functions within its own code, allowing use of popular C libraries natively in Pekoe (such as SDL).
This will be expanded upon when the compiler is more developed, and will be used to implement the standard library.