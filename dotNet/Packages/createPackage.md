# [.NET class library](https://docs.microsoft.com/en-us/dotnet/core/tutorials/library-with-visual-studio-code)

A class library defines types and methods that are called by an application

# Create a solution

Run this command on your computer terminal 

```bash
dotnet new sln
```

## Create class library

The class is made for the functionality to create random persons for the personsApi and the personsConsoleApp

```bash
dotnet new classlib -o PersonsUtilityLibrary
```

## Add Library project to solution

```bash
dotnet sln add StringLibrary/StringLibrary.csproj
```

## Add your code

On `Class1.cs` add the code to generate random persons

```cs
namespace PersonsUtilityLibrary;
public class PersonsLibrary
{
    private static string[] names;
    private static string[] lastNames; 

    public static readonly Dictionary<Int16, string> departments = new Dictionary<Int16, string>();

    public static Person GeneratePersonPropierties()
    {

    }

    private static float GenerateHeight(Random random)
    {

    }

    private static float GenerateWeight(Random random)
    {

    }


    private static string GenerateName(Random random) 
    {

    }

    private static string GenerateDepartment(Random random)
    {

    }

    private static string GenerateLastName(Random random)
    {

    }

    private static DateTime GenerateRandomDate(Random random)
    {

    }
}
```

## Build your app

run
```bash
dotnet build
```

# Use the solution

On PersonsApi or PersonsConsoleApp you need to add a reference of your package like this:

```bash
dotnet add .\PersonsApi.csproj reference "PersonUtilities/PersonsUtilityLibrary/PersonsUtilityLibrary.csproj"
```

and you will see

```bash
Reference `..\PersonsUtilityLibrary\PersonsUtilityLibrary.csproj` added to the project.
```

# Try the solution

On PersonsApi or PersonsConsoleApp where the old code when the persons are generated just need to import with `using` the name of the library and use the methods.


```cs
//PersonService.cs

using PersonsApi.Models;
using System.Collections.Generic;
using PersonsUtilityLibrary;
namespace PersonsApi.Service
{
    public static class PersonService
    {
        private static int PersonIdSeed = 1000;

        internal static List<Person> Persons { get; }

        static PersonService()
        {
            var person = PersonsLibrary.GeneratePersonPropierties();
            person.Number = PersonIdSeed++;
            Persons = new List<Person>
            {person};
        }

        /*
            Now when use the package with using PersonsUtilityLibrary.
            it's possible to do PersonsLibrary.GeneratePersonPropierties();
        */

        public static Person GenerateRandomPerson()
        {
            var person = PersonsLibrary.GeneratePersonPropierties();
            person.Number = PersonIdSeed++;
            Persons.Add(person);
            return person;
        }
    }
}
```