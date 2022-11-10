# Classes .net libraries

## Namespace

Think of a namespace as the last name, surname or "family name" for a type. A class contains the code that implements a type. **Classes are organized into namespaces to prevent naming collisions.** After all, when there are thousands of classes, it's possible that there might be a need to reuse a class name. The namespace helps to make sure no two classes have the same full name.

If you want to create a library for your a personal project that you are working on when you import the library with `using` the name space is crucial to understand where is located the resource also to avoid problems with others library

for example the library is called `MyBestLibrary` is because on all your code you put 

```cs
namespace MyBestLibrary
{

}
```
now on your project `MyBestProject` you need to use your `MyBestLibrary` so C# to identify it required the use of the namespace

```cs 
using MyBestLibrary;

namespace MyBestProject
{

}
```

### How to call methods

For example `Console.WriteLine();` has this structure:
* `Console` is the class name
* `.` is to get a member of the class or method
* `WriteLine` is the method name
* `()` is the invocation operator for the method.

inside the invocator operator you can put the different resourses or values that is required. remember to search the documentation on the method because most of the time these method use function overloading.

### Stateful versus stateless methods

[Also see](https://docs.microsoft.com/en-us/learn/modules/csharp-call-methods/3-call-methods)

In computing, **state describes the condition of the execution environment at a specific moment in time**. As your code executes line by line, values are stored in variables. At any moment during execution, the current state of the application is the collection of all values stored in memory.

**Some methods don't rely on the current state of the application to work properly. In other words, stateless methods are implemented so that they can work without referencing or changing any values already stored in memory. Stateless methods are also known as static methods.**

For example, the Console.WriteLine() method doesn't rely on any values stored in memory. It performs its function and finishes without impacting the state of the application in any way.

**Other methods, however, must have access to the state of the application to work properly. In other words, stateful methods are built in such a way that they rely on values stored in memory by previous lines of code that have already executed. Or they modify the state of the application by updating values or storing new values in memory. They're also known as instance methods.**

Stateful (instance) methods keep track of their state in fields, which are variables defined on the class. Each new instance of the class gets its own copy of those fields in which to store state.

**A single class can support both stateful and stateless methods.** However, when you need to call stateful methods, you must first create an instance of the class so that the method can access state.

## Code blocks

[Code blocks define methods, classes, and namespaces](https://docs.microsoft.com/en-us/learn/modules/csharp-code-blocks/3-method-class-namespace)

```cs
using System;

namespace MyNewApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

There are three levels of code blocks:

* method Main()
* class Program
* namespace MyNewApp

### Method

[Recommended](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods)

is a code block that is a unit of execution. In other words, once the method is called by its name, the entire method will execute until:

* the runtime encounters the return keyword.
* the runtime encounters an exception and can't continue.
* the runtime successfully executes each line of code in the method.

### Class 

is a **container for members like methods, properties, events, fields, and so on.** 

### Namespace

**disambiguates class names.** There are so many classes in the .NET Class Library that it's possible to have two classes with the same name. The namespace ensures you can instruct the compiler which class and method you want to work with by also specifying a namespace.

## Access Modifiers 

* Add link *