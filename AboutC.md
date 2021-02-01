# Intros

## Features:
* Dos: 
  * Procedural or functional (not object-oriented)
  * Fully compiled to machine code (not bytecode)
  * Direct manipulation of memory (pointers)
  * No garbage collection --> manual explicit memory management
* Don't:
  * No notion of classes or objects
  * No Encapsulation. All memory is accessible and modifiable
  * No class inheritance
* Four different general categories of statments:
  * Declarations
  * Data movement
  * Arithmetic/Logival operations
  * Control-flow
## Versions:
* **-ansi** We use ANSI C standardized in 1989 by the American National Standards Institute --> C89
* other C version like International Standards Organization (ISO) -- C90 

## Compile time and Run time concept
* Static, Compile time: the time that the program is being built or compiled
  * syntax error: invalid program
  * linkage error: **TODO!**
* Dynamic, Runtime: the time while the program is runnning
  * semantic errors: valid program, but it does not do as we expected

## Preprocessor

```
#include <stdio.h> /*Preprocessor directives*/

void main (int arc, char **arv) {
  printf("Hello, ");
  printf("World!\n");
}
```

The preprocessor looks in the area on the disk where library files are kept the file with the name `stdio.h`. And then replaces the directive in the source file with **copy of the contents**  of the specified header file.

### Fun facts:
* File locations of the two header files:
 * */usr/include/stdio.h*
 * */usr/include/stdlib.h*
* Commemts:
  * // Single line comments not supported by ANSI C
  * Nested comments not supported
  * Must use /* blablabla comment */ 
* Preprocessor can replace macros: the names of these macros get replaced with the code that they are defined to represent
  * `#define  string1 string2`
  * `string1` cannot contain any white space characters (spaces, tabs, new lines), **but `string2` can**
  * any time `string1` shows up in the source code, the preprocessor will replace it with `string2`
* Preprocessor directives are not statements
* C programs consist of zero or more preprocessor directives, along with declarations and definitions of 
    * one or more functions
    * zero or more variables declared or defined outside any function

### About header files:
The header file may contain many things, nbut typically:
* one or more function **prototypes** --> return type & pararmeters of functions --> necessary for error checking during compilation
* **no code, merely prototypes**

## Declarations & Definitions 

A variable must be declared **(not necessarily defined)** before it can be referenced in a non-declarative statement
Afunction must be declared **(not necessarily defined)** before it can be referenced in a non-declarative statement (called or invoked)

### Declarations

Type information only, no values

* Varaible: `int x;`: tell compiler the type of the variable, not its value
* Function: `int foo(int, int)`: tell compiler the return type and types of its params, names of the params are optional
* **A varibale can only be declared a single time in a given block, while a function can be declared multiple times, as long as all of declarations are consistent --> identical with respect to types**

### Definitions

Type information, and value

* Variable `int x = 10;`: tell compiler the type and initial value of the variable
* Function: return type, params types, and function body
* **Both variable and function can only be defined once in a C program**
* **definition is also a declaration**


## main

Note every C program **must** have **exactly one** main function, and program always begins in this function
Java has a main method, but it is in a class. Note C has no classes! No methods! 

## Functions

* A function prototype is a declaration or definition, which includes:
  * number of arguments
  * types of arguments
  * type of value the function returns

* Same as Java, C passes arguments to functions by value
* We can, modify the values by passing a pointer instead

### Construct of a function

* Declare all your variables at the beginning of your blocks
* file scope, any function declared within a file can be declared from anywhere in the same file after the point at which it is declared
* Functions consist of on or more blocks. Blocks can be empty.
* Nested blocks are fine, but no nested functions!











