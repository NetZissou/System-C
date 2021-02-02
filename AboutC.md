# C Intros

1) hello.c -- source code, plain text\n
   `%gcc -c hello hello.c`\n
2) Preprocessor `.c` + `.h` = `.i` --> ultimate source code (#include expanded #defines replaced)\n
3) Compiler `.i` --> `.s` --> assembler source code\n
4) Assembler assembly code `.s` --> `.o` --> object file, close to executable, some unresolved symbols\n
5) Link Editor object code `.o` + library links `a.out` --> executable code
6) hello (executable code) -- %hello will execute the program

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


# C Overview

## Basic Data Types

~8, ~16, ~32, ~32 bits
* Integer Types

* Floating point Types

char - smallest addressable unit, **always** 8 bits; guaranteed to always be one byte

sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long)
sizeof(float) <= sizeof(double) <= sizeof(long double)

Beside the basic types, there is a conceptually infinite class of derived types constructed from the fundamental types in the following ways:
* array of objects (variables or derived types) of a given type
* pointers to objects of a given type
* structures containing a sequence of objects of various types
* unions capable of containing any of one of sereral objects of various types
This can be applied recursively...

## Constants

![GitHub Logo](/images/constants.jpeg)

### Declaration of Constants
Format: front or back both the keyword
```
float const PI = 3.141593f;
const float PI = 3.141593f;
```
* The compile treats these constant as **read-only variable**, which indicates that you must initialize the constant before you don't have a chance.
* Uppercase

### Symbolic Constants
A name that substitutes for a value that cannot be changed, which can be used to define a:
* Constant
* Statement
* Mathematical expression
`#define <name> <value>` --> `#define AREA 3.141593*r*r`
```
#define PI 3.1415926
#define TRUE 1
```
**Note: no semi-colon is used for preprocessor directives**
All occurrences are replaced by the preprocessor before the program is compiled by the compiler.

## Variable Declarations
* Format: type identifier, identifier, identifier...
* Initial value: not required unless it's a constant
```
int i, j = 5,k;
char code, category;
const float PI = 3.214214f;
```
* Type conversion: **casting**
   * Casting larger types to smaller types is dangerous
   * To cast a variable explicitly: name = (type) identifier
   ```
   /* int 32bits, always char 8bits
   int i = 65;
   char ch; /*-128 to 127*/
   ch = (char)i; 
   ```

## Keywords
keywords are reserved identifiers to have a particular meaning.

## Operators
* **classified according to the number of operands which they take**
   * unary operators
   * binary operators
   * one ternary operator --> the conditional operator `?:`
* Operands are expressions:
   * constants
   * variables
   * or expressions which contain one or more operators
* Expressions will always be evaluated --> has a value, a type

### Precedence and Associativity
* **Precedence** refers to the **relationship between two operators** in terms of the **order** in which the operations are performed
   * a binary relation --> pairs of operators
   * Binary operators are adjacent if they have one operand in common `3+5*6`
   * unary operators are adjacent if they have the operand
* Enforce a precedence --> using parentheses
* when two adjacent operators have the same prededence --> **associativity**
   * **L-R**: operation specified by the leftmost operator is done first
   * **R-L**: vice versa
Example:
suppose *a = 1, b = 3, and c = 5* and we have `d = ++a*c+b++;`
Note: ++a evaluate before the rest is done, b++ evaluate after the operation
* Parenthesize unary operators:
note that the compiler does the binary operation with the highest precedence first, expressions with unary operators are not evaluated until they need to be.
```
d = (++a) * c + (b++)
```
Not the precendence of binary operators are: 
`*` --> `+` --> `=`
* Now add the rest of the parentheses:
```
d = ( ((++a) * c) + (b++) )
```
* Value of expression
   * ++a -> 2
   * c --> 5
   * **b++ --> 3**
   * d = (2*5) + 3 = 13
   * a = 2, **b = 4**, c = 3
   
### Assignment operators
* What is assignment in C? **Assignments are expressions**, which indicates that like any other expression the assignment **has a value**., which is the value of the rightmost expression.
* Assignment has the lowest precedence expect the comma operator
* Embeded assignments: associativity
   * `a = b = 1;` /* R-L  multiple assignment*/
   * Others like `+=, -=, *=, /=, %=` same associativity - **R-L**
* And note using an assignment orperator(=) is legal if we used that for equality(==). This is not a syntax error and our compiler will not fail.

**= VS ==**
* desired: `if(tokens == 6)` 
* drop a = sign: `if(tokens=6)` always be true
Instead, good practice is to code code defensively
* `if (6 == tokens)`
* `if (6 = tokens)` <-- this will not compile

### Unary Operators
* Always higher than Binary operators
* `++a` and `a++` both have the behavior of a = a=1
* `++a`: a is incremented **BEFORE**  a is evaluated in the expression
* `a--`: a is incremented **AFTER**  a is evaluated in the expression
```
#include <stdio.h>
int main() {
   int a = 1;
   printf("a is %d", ++a); /* print result: 2 */
   return 0;
}
```

```
#include <stdio.h>
int main() {
   int a = 1;
   printf("a is %d", a++); /* print result: 1 */
   return 0;
}
```
   

 
   
   
   



