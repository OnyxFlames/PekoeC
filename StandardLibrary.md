# Standard Library

* [IO](#IOLib)
* [FileIO](#FileIO)
* [Format](#Format)
* [Math](#MathLib)
* [Error](#ErrorLib)
* [String](#StringLib)
* [Memory](#Memory)
* [SIMD](#SIMD)

## IO
The IO library provides reading and writing functionality for the console.
The function declarations are as follows:

```c
// writes Null-terminated string into stdout, returns # of characters written
write : (str : u8*) -> i32;

// returns Null-terminated string read froms stdin
read : () -> u8*;

// writes count characters from string into stdout
write : (str : u8*, count : i32) -> i32;

// reads count characters from stdin and returns as array
read : (count : i32) -> u8*;

// write character to stdout
writechar : (c : u8) -> void;

// read character from stdin
readchar : () -> u8;

```

## FileIO
The FileIO library provides similar functionality as the IO library but focuses on files.

The FileIO libary also provides a means to open, modify, and close file handles.

```c
FileHandle : class
{
    open : (name : u8*) -> bool;
    close : () -> void;
    is_open : () -> bool;

    write : (str : u8*) -> i32;
    read : () -> u8*;

    write : (str : u8*, count : i32) -> i32;
    read : (count : i32) -> u8*;

    // get size of file in bytes
    size : () -> u64;
};
```

## Format
```
format : (str : u8*, ...) -> u8*;
```
## Math
Basic math functions inherited from C
```c
// 32 bit
acos    : (x : f32) -> f32;
asin    : (x : f32) -> f32;
atan    : (x : f32) -> f32;
atan    : (y : f32, x : f32) -> f32;
cos     : (x : f32) -> f32;
cosh    : (x : f32) -> f32;
sin     : (x : f32) -> f32;
sinh    : (x : f32) -> f32;
tanh    : (x : f32) -> f32;
exp     : (x : f32) -> f32;
frexp   : (x : f32, e : i32*) -> f32;
ldexp   : (x : f32, e : i32) -> f32;
log     : (x : f32) -> f32;
log10   : (x : f32) -> f32;
modf    : (x : f32, i : f32*) -> f32;
pow     : (x : f32, y : f32) -> f32;
sqrt    : (x : f32) -> f32;
ceil    : (x : f32) -> f32;
fabs    : (x : f32) -> f32;
floor   : (x : f32) -> f32;
fmod    : (x : f32, y : f32) -> f32;
// 64 bit
acos    : (x : f64) -> f64;
asin    : (x : f64) -> f64;
atan    : (x : f64) -> f64;
atan    : (y : f64, x : f64) -> f64;
cos     : (x : f64) -> f64;
cosh    : (x : f64) -> f64;
sin     : (x : f64) -> f64;
sinh    : (x : f64) -> f64;
tanh    : (x : f64) -> f64;
exp     : (x : f64) -> f64;
frexp   : (x : f64, e : i32*) -> f64;
ldexp   : (x : f64, e : i32) -> f64;
log     : (x : f64) -> f64;
log10   : (x : f64) -> f64;
modf    : (x : f64, i : f64*) -> f64;
pow     : (x : f64, y : f64) -> f64;
sqrt    : (x : f64) -> f64;
ceil    : (x : f64) -> f64;
fabs    : (x : f64) -> f64;
floor   : (x : f64) -> f64;
fmod    : (x : f64, y : f64) -> f64;
```

## Error

## String

## Memory
Allocation, endianess, byte swapping, and more fun memory stuff
```
allocate : (size : u32) -> u8*;
deallocate : (mem : u8*) -> void;
reallocate : (mem : u8*) -> u8*;

isLittleEndian : () -> bool;
isBigEndian : () -> bool;

byteswap : (bytes : i16) -> i16;
byteswap : (bytes : u16) -> u16;
byteswap : (bytes : i32) -> i32;
byteswap : (bytes : u32) -> u32;
byteswap : (bytes : i64) -> i64;
byteswap : (bytes : u64) -> u64;
```


## SIMD
Single-Instruction-Multiple-Data operation functions, compiles to supported SIMD instructions if the compiler's host supports it
```

```