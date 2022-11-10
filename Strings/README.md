# Strings 

Strings on C# is a Reference type but it doesent require to use the keyword `new()` to make it more easy to and make it more similar to others languaje like C++ or Java.

Strings have lots of functionalities to explore to process the data contained on strings

here we are going to explore some of the functionalities that c# gives to process and using string

## Verbatim String Literal

[Visit @ (C# Reference)](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/verbatim)

A verbatim string literal will keep all whitespace and characters without the need to escape the backslash `\t \n`. To create a verbatim string, use the @ directive before the literal string. Two consecutive double-quote characters ("") are printed as a single double-quote character (") in the output string.

```cs
Console.WriteLine(@"   hello   
    This is an example
        Using
            Verbatim");
``` 
**Result**
```bash
   hello   
    This is an example
        Using
            Verbatim
```

## String Formatting 

[Visit String.Format Method](https://docs.microsoft.com/en-us/dotnet/api/system.string.format)

## String Interpolation

[Resource String Interpolation](https://docs.microsoft.com/en-us/learn/modules/csharp-basic-formatting/4-exercise-string-interpolation)

String interpolation combines multiple values into a single literal string by using a "template" and one or more interpolation expressions. An interpolation expression is a variable surrounded by an opening and closing curly brace symbol { }. The literal string becomes a template when it's prefixed by the $ character. 

Interpolate is similar to JavaScript string formatting, the principal use of interpolation is to avoid the long and extensive contatenation.

```cs 
string message = "Hello: ";
string message += Username;
string message += "This is an exmaple";

string message = $"Hello: {Username} This is an example";

```

### Verbatim + Interpolation

To mix Verbatim and Interpolation is required only to use `@` and `$` at the same time

```cs
string projectName = "First-Project";
Console.WriteLine($@"C:\Output\{projectName}\Data");
```

## Formatting currency

Composite formatting and string interpolation can be used to format values for display given a specific language and culture. In the following example, the :C currency format specifier is used to present the price and discount variables as currency.

```cs
decimal price = 123.45m;
int discount = 50;
Console.WriteLine($"Price: {price:C} (Save {discount:C})");
```

Using these string formatting features are dependent on the computing culture. In this context, the term "culture" refers to the country and language of the end user. The culture code is a five character string that computers use to identify the location and language of the end user to ensure certain information like dates and currency can be presented properly.

## Formatting numbers

When working with numeric data, you may want to format the number for readability by including commas to delineate thousands, millions, billions, and so on.

The N numeric format specifier will do this.

```cs
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N} units");
```

If you want to display more precision, you can do that by adding a number after the specifier. The following code will display four digits after the decimal point using the N4 specifier.

```cs
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N4} units");
```

Use the P format specifier to format percentages. Add a number afterwards to control the number of values displayed after the decimal point.

```cs
decimal tax = .36785m;
Console.WriteLine($"Tax rate: {tax:P2}");
```