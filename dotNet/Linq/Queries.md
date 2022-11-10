# [Basic LINQ Query Operations (C#)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/basic-linq-query-operations)

## Obtaining a Data Source

In a LINQ query, the first step is to specify the data source. In C# as in most programming languages a variable must be declared before it can be used. In a LINQ query, **the `from` clause comes first in order to introduce the data source (persons) and the range variable (cust).**

```cs
var queryAllPersons = from person in PersonService.Persons select person;
```

### Note

Array list is not supported please visit [How to query an ArrayList with LINQ (C#)
](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq)

## Filtering

**The filter causes the query to return only those elements for which the expression is true. The result is produced by using the `where` clause.**

```cs
IEnumerable<Person> = from person in PersonService.Persons 
    where person.Department == "Antioquia"
    select person;
```

also support `&&` and `||` to made the filtering

```cs
IEnumerable<Person> = from person in PersonService.Persons 
    where person.Department == "Antioquia" || person.Department == "Amazonas"
    select person;

IEnumerable<Person> = from person in PersonService.Persons 
    where person.Department == "Antioquia" && person.Height == 1.85
    select person;
```

## Ordering

The orderby clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted. For example, the following query can be extended to sort the results based on the Name property. Because Name is a string, the default comparer performs an alphabetical sort from A to Z.

```cs
var queryLondonCustomers3 =
    from person in PersonService.Persons 
    where person.Department == "Antioquia"
    orderby person.Name ascending
    select person;
```

## Grouping

The group clause enables you to group your results based on a key that you specify. For example you could specify that the results should be grouped by the Deparment so that all customers from Antioquia or Amazonas are in individual groups. In this case, person.Deparment is the key, the result will be a list of lists where in each list is the peopulation by each deparment

```cs
var queryPersonByDeparment =
    from person in PersonService.Persons    
    group person by person.Deparment;

foreach (var personGroup in queryPersonByDeparment)
{
    Console.WriteLine(personGroup.Key);
    foreach (Person person in personGroup)
    {
        Console.WriteLine("    {0}", person.Name);
    }
}
```

### Into

If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further. The following query returns only those groups that contain more than two customers:

```cs
var queryPersonByDeparment =
    from person in PersonService.Persons    
    group person by person.Deparment into departGroup
    where departGroup.Count() > 2
    orderby departGroup.Key
    select departGroup;
```

## Joining

Join operations create associations between sequences that are not explicitly modeled in the data sources. For example you can perform a join to find all the customers and distributors who have the same location. In LINQ the join clause always works against object collections instead of database tables directly.

```cs
var innerJoinQuery =
    from cust in customers
    join dist in distributors on cust.City equals dist.City
    select new { CustomerName = cust.Name, DistributorName = dist.Name };
```