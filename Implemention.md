# Implementation

## Name Mangling
To enable function overloading, Pekoe will structurely mangle function names based on their type signature, which will also be used to look up matching function definitions when compiling.
This may lead to Pekoe code being more type strict (Eg. function (i32, i16) won't accept (i16, i32) without explicit casting)

To prevent risk of name shadowing in the emitted code, all names may be mangled similarly when compiling.

## Mangle rules
* Parameters are prefixed with p
* Return types are prefixed with r
* Class types are prefixed with c
* Pointer types are suffixed with ptr
* Array types are suffixed with arr

A hypothetical example:
```
mul : (x : i32, y : i32) -> u32
{
    return x * y;
}
```
will compile to
```c
uint32_t func_mul_pi32_pi32_ru32(int32_t x, int32_t y)
{
    return x * y;
}
```

This will apply to standard library, and user defined types as well.

```
string : class
{
    // ... 
};

clearString : (str : string) -> string
{
    // ...
};
```
Would compile to:

```c
typedef struct
{
    // ...
} cstring;

cstring func_clearString_pcstring_rcstring(cstring str)
{
    // ...    
}
```

### Note: class objects may need to default to passing by pointer to prevent pass-by-value causing weird behavior

## Interacting with native C code
Pekoe will *not* mangle function calls labeled as C code, as those functions are expected to remain intact when compiling to the target language. See Language.md #InteractingWithC