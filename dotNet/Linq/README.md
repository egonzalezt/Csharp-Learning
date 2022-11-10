# [Language Integrated Query (LINQ) (C#)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/)

Language-Integrated Query (LINQ) is the name for a set of technologies based on the integration of query capabilities directly into the C# language. Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support. 

For a developer who writes queries, the most visible "language-integrated" part of LINQ is the query expression. Query expressions are written in a declarative query syntax. **By using query syntax, you can perform filtering, ordering, and grouping operations on data sources with a minimum of code.**

You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and **any collection of objects that supports IEnumerable or the generic IEnumerable<T> interface.** LINQ support is also provided by third parties for many Web services and other database implementations.

```cs
// Specify the data source.
int[] scores = { 97, 92, 81, 60 };

// Define the query expression.
IEnumerable<int> scoreQuery =
    from score in scores
    where score > 80
    select score;

// Execute the query.
foreach (int i in scoreQuery)
{
    Console.Write(i + " ");
}

// Output: 97 92 81
```

# Microsoft Recommends

* As a rule when you write LINQ queries, we recommend that you use query syntax whenever possible and method syntax whenever necessary. There is no semantic or performance difference between the two different forms. Query expressions are often more readable than equivalent expressions written in method syntax.

* At compile time, query expressions are converted to Standard Query Operator method calls according to the rules set forth in the C# specification. Any query that can be expressed by using query syntax can also be expressed by using method syntax. However, in most cases query syntax is more readable and concise.


# [Three Parts of a Query Operation](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries#three-parts-of-a-query-operation)

All LINQ query operations consist of three distinct actions:

* Obtain the data source.

* Create the query.

* Execute the query.

```cs
class IntroToLINQ
{
    static void Main()
    {
        // The Three Parts of a LINQ Query:
        // 1. Data source.
        int[] numbers = new int[7] { 0, 1, 2, 3, 4, 5, 6 };

        // 2. Query creation.
        // numQuery is an IEnumerable<int>
        var numQuery =
            from num in numbers
            where (num % 2) == 0
            select num;

        // 3. Query execution.
        foreach (int num in numQuery)
        {
            Console.Write("{0,1} ", num);
        }
    }
}
```

# Forcing Immediate Execution

Queries that perform **aggregation functions over a range of source elements must first iterate over those elements.** Examples of such queries are **Count, Max, Average, and First.** These execute without an explicit foreach statement because the query itself must use foreach in order to return a result. Note also that these types of queries return a single value, not an IEnumerable collection. The following query returns a count of the even numbers in the source array:

```cs
var evenNumQuery =
    from num in numbers
    where (num % 2) == 0
    select num;

int evenNumCount = evenNumQuery.Count();
```

# [IEnumerable<T> variables in LINQ Queries](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/linq-and-generic-types#ienumerablet-variables-in-linq-queries)

LINQ query variables are typed as [`IEnumerable<T>`](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ienumerable-1?view=net-6.0) or a derived type such as `IQueryable<T>`. When you see a query variable that is typed as IEnumerable<Customer>, **it just means that the query, when it is executed, will produce a sequence of zero or more Customer objects.**

```cs
IEnumerable<Customer> customerQuery =
    from cust in customers
    where cust.City == "London"
    select cust;

foreach (Customer customer in customerQuery)
{
    Console.WriteLine(customer.LastName + ", " + customer.FirstName);
}
```

but there is no problem if the programer let the compiler infer the data type `var customerQuery` 