# Standard Library

* [IO](#IOLib)
* [FileIO](#FileIO)
* [Format](#Format)
* [Math](#MathLib)
* [Error](#ErrorLib)
* [String](#StringLib)

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