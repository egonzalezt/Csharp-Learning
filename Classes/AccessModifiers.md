# Access Modifiers

All types and type members have an accessibility level. **The accessibility level controls whether they can be used from other code in your assembly or other assemblies:**

* **public:** The type or member can be accessed by any other code in the same assembly or another assembly that references it. The accessibility level of public members of a type is controlled by the accessibility level of the type itself.

* **private:** The type or member can be accessed only by code in the same class or struct.

* **protected:** The type or member can be accessed only by code in the same class, or in a class that is derived from that class.

* **internal:** The type or member can be accessed by any code in the same assembly, but not from another assembly. In other words, internal types or members can be accessed from code that is part of the same compilation.

* **protected internal:** The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived class in another assembly.

* **private protected:** The type or member can be accessed by types derived from the class that are declared within its containing assembly.


Class and record members (including nested classes, records and structs) can be declared with any of the six types of access. Struct members can't be declared as protected, protected internal, or private protected because structs don't support inheritance.

## Also visit 

[Access Modifiers - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)

[Operator overloading - C# reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/operator-overloading)

[Accessibility Levels - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/accessibility-levels)


Types
* [public keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public)
* [private keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private)
* [protected keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected)
* [internal - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/internal)
* [protected internal - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected-internal)
* [private protected - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private-protected)
	* [InternalsVisibleToAttribute Class (System.Runtime.CompilerServices) | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.compilerservices.internalsvisibletoattribute?view=net-6.0)
