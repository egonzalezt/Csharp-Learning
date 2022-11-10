# Types and variables

## What is a data type?

A data type is a programming language construct that defines **how much memory to reserve for a value.**

## Type

A type defines the structure and behavior of any data in C#.

## Variable
A variable is a label that refers to an instance of a specific type.

## Types of type

There are two kinds of types in C#: **value types** and **reference types**. 

### Stack vs Heap

The fundamental difference between value and reference types concerns where those values are temporarily stored in memory as your application executes. Where the value is stored affects how the .NET runtime manages the life of the value including its declaration (birth), assignment and retrieval (life), and finalization (death). This, in turn, impacts the syntax you use when working with either a value type or a reference type.

Variables of value types directly contain their data, C# store variables on memory but depend of the type those variables or data are stored on two places **STACK** or **HEAP**

In short words stack store directly the value, for example `int value = 10;` number 10 is store directly on the stack instead of heap that store a reference or the memory address on the stack, that address points to the location where is store the value on the heap


### [Value Types](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types)

Variables of value types directly contain their data.

### [Reference Types](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/reference-types)

Variables of reference types store references to their data. With reference types, it's possible for two variables to reference the same object and possible for operations on one variable to affect the object referenced by the other variable. With value types, the variables each have their own copy of the data, and it isn't possible for operations on one to affect the other.

### Magic table of Types

C# like other compiled languajes use an strong data type declaration insted of languajes like Python or JavaScript. The magic table shows the different data types and split by whom is Value or Reference type.

#### Value types

[Choose the right data type](https://docs.microsoft.com/en-us/learn/modules/csharp-choose-data-type/6-choose-right-data-type)

##### Simple types
* Signed integral: sbyte, short, int, long
    * Unsigned integral: byte, ushort, uint, ulong
    * Unicode characters: char, which represents a UTF-16 code unit
    * IEEE binary floating-point: float, double
    * High-precision decimal floating-point: decimal
    * Boolean: bool, which represents Boolean values—values that are either * true or false
* Enum types
    * User-defined types of the form enum E {...}. An enum type is a distinct type with named constants. Every enum type has an underlying type, which must be one of the eight integral types. The set of values of an enum type is the same as the set of values of the underlying type.


* Struct types
    * User-defined types of the form struct S {...}
* Nullable value types
    * Extensions of all other value types with a null value
* Tuple value types
    * User-defined types of the form (T1, T2, ...)

##### Reference types
* Class types
    * Ultimate base class of all other types: object
    * Unicode strings: string, which represents a sequence of UTF-16 code units
    * User-defined types of the form class C {...}
* Interface types
    * User-defined types of the form interface I {...}
* Array types
    * Single-dimensional, multi-dimensional, and jagged. For example: int[], int[,], and int[][]
* Delegate types
    * User-defined types of the form delegate int D(...)

## Implicitly typed local variables
Please visit *put URL *

## Extra

More information that I found interesting 

* [in parameter modifier - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/in-parameter-modifier)
* [ref keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/ref)
* [out parameter modifier - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/out-parameter-modifier)

## References

Part of this documentation is taken from:

* [A tour of the C# language](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
* [8 Types](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/types) (Recommended)