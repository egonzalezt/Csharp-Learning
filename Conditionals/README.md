# [Conditionals](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/tutorials/branches-and-loops-local?WT.mc_id=Educationalcsharp-c9-scottha#make-decisions-using-the-if-statement)

If you need to take a desicion to choose one or other option on programming conditionals is the best option to do it.

## If statement

C# use the if statement and another reserved words to make conditionals (others programming languajes the sintax is exactly the same like C++)

```cs
int number = 21;

if(number%2!=0)
{
    Console.WriteLine($"{number} is odd number");
}
```

the condition says if the modulus of 2 is different of zero means that the number is odd but, what happens with the even numbers?

## Else Statement

Else is used to execute a code block if the `if` statement it´s not true 

```cs
int number = 20;

if(number%2!=0)
{
    Console.WriteLine($"{number} is odd number");
}else
{
    Console.WriteLine($"{number} is even number");   
}
```

In this case if the number does not meet the condition executes the code block inside `else` statement, but if the number is a prime number like 7.

## Else If Statement

If the `if` statement fails but you need to check other condition is required to use `else if` because `else` statement can´t prove any kind of condition.

```cs
int number = 7;

if(number%2==0)
{
    Console.WriteLine($"{number} is even number");
}else if(number%2!=0 && number == 7)
{
    Console.WriteLine($"{number} is odd number and prime number");   
}else
{
    Console.WriteLine($"{number} is odd number");   
}
```

## [Ternary Operator](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)

Ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to true or false, as the following example shows:

```cs
string GetWeatherDisplay(double tempInCelsius) => tempInCelsius < 20.0 ? "Cold." : "Perfect!";
Console.WriteLine(GetWeatherDisplay(15));  // output: Cold.
Console.WriteLine(GetWeatherDisplay(27));  // output: Perfect!
```

## [Operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/)

To make logical operations it´s required to work with logical operators or numerical operators.

Check these resources from Microsoft

* [Comparison operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators)
* [Boolean logical operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators)
* [Equality operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/equality-operators)
* [Bitwise and shift operators](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators)