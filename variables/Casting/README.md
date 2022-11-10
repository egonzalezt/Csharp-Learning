# [Casting ´n´ Conversion](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions)

## String to int (the most common)

On this example it´s imposible to sum 2 + "4" because 4 is type string and 2 is type int for that reason the compiler will return an error.

```cs
int first = 2;
string second = "4";
int result = first + second; //code breaks
Console.WriteLine(result); 
```

The C# compiler sees a potential problem in the making. The variable second is of type string, so it might be set to a different value like "hello". If the C# compiler attempted to convert "hello" to a number that would cause an exception at runtime. To avoid this possibility, the C# compiler will not implicitly perform the conversion from string to int for you.


**If you intend to perform addition using a string, the C# compiler requires you to take more explicit control of the process of data conversion.** In other words, it forces you to be more involved so that you can put the proper precautions in place to handle the possibility that the conversion could throw an exception.

If you need to change a value from the original data type to a new data type and the change could produce an exception at run time, you must perform a data conversion.

**To perform data conversion, you can use one of several techniques:**

* Use a helper method on the data type
* Use a helper method on the variable
* Use the Convert class' methods

## Widening 

The term widening conversion means that you are **attempting to convert a value from a data type that could hold less information to a data type that can hold more information.** In this case, you'll lose no information. So, **an example of this would be converting a value stored in a variable of type int and now converting that value into a variable of type decimal.**

If you were to print out the two values, you would likely notice no difference.

When you know you'll be performing a widening conversion, **you can rely on implicit conversion. Implicit conversion is handled by the compiler.**

## Narrowing

The term narrowing conversion means that you're **attempting to convert a value from a data type that can hold more information to a data type that can hold less information.** In this case, **you may lose information such as precision (that is, the number of values after the decimal point).** An example of this would be converting value stored in a variable of type decimal and now convert that value into a variable of type int. If you were to print out the two values, you would possibly notice the loss of information.

## Methods

### ToString()

Use ToString() to convert a number to a string

**Every data type variable has a ToString() method**. What the ToString() method does depends on how it's implemented on a given type. However, on most primitives, it performs a widening conversion. 

### Explicitly converting a string to a number

**Most of the numeric data types have a Parse() method**, which will **convert a string into the given data type.** In this case, we'll use the Parse() method to convert two strings into int values, then add them together.

### Data Conversion using the Convert class

The Convert class has many helper methods to convert a value from one type into another. In the following code example, we'll convert a couple of strings into values of type int.

```cs
string value1 = "5";
string value2 = "7";
int result = Convert.ToInt32(value1) * Convert.ToInt32(value2);
Console.WriteLine(result);
```

So, when should we use the Convert class? The **Convert class is best for converting fractional numbers into whole numbers (int) because it rounds up the way you would expect.**

### TryParse()

The TryParse() method does several things simultaneously:

**It attempts to parse a string into the given numeric data type.** If successful, it will store the converted value in an `out` parameter. It **returns a bool to indicate whether the action succeeded or failed.**

#### [What is an out parameter?](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/out-parameter-modifier)

Methods can return a value or return "void", meaning they return no value. Methods can also return values through out parameters, which are defined just like an input parameter, but include the out keyword.

```cs
string value = "102";
int result = 0;
if (int.TryParse(value, out result))
{
    Console.WriteLine($"Measurement: {result}");
}
else
{
    Console.WriteLine("Unable to report the measurement.");
}
```
Use TryParse could be a better way to solve possible errors for handling errors and avoid possible breaks on the code.