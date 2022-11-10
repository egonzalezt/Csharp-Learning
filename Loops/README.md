# [Loops](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/tutorials/branches-and-loops-local?WT.mc_id=Educationalcsharp-c9-scottha#use-loops-to-repeat-operations)

Sometimes you need to repeat and repeat some fragment of code for example 

```cs
Console.WriteLine($"1x1 = {1*1}");
Console.WriteLine($"1x2 = {1*2}");
Console.WriteLine($"1x3 = {1*3}");
Console.WriteLine($"1x4 = {1*4}");
Console.WriteLine($"1x5 = {1*5}");
Console.WriteLine($"1x6 = {1*6}");
Console.WriteLine($"1x7 = {1*7}");
Console.WriteLine($"1x8 = {1*8}");
Console.WriteLine($"1x9 = {1*9}");
Console.WriteLine($"1x10 = {1*10}");
```

using loops this work is much easier:
```cs
for(int i=0;i<=10;i++)
{
    Console.WriteLine($"1x{i} = {1*i}");
}
```

## For Loop

Use for loop to iterate through the code x times because you know exactly the times to repeat

```cs
for(int i=0;i<=10;i++)
{
    Console.WriteLine($"1x{i} = {1*i}");
}
```

## For Each

Use for each to iterate on list, dictionaries, arrays, etc.

```cs
int[] numbers = {1,2,3,4,5,6,7,8,9,10};

foreach(var number in numbers)
{
    Console.WriteLine(number);
}
```

## While

Sometimes you don´t know how many times you need to repeat some segment of code for that reason you need to use while loop, when something happens or some condition occurs the loop stops.

```cs
var title = "Name";
Console.Write($"{title}: ");
var data = Console.ReadLine();
while(true){
    if(data!=null)
    {
        break;
    }else{
        Console.WriteLine("Value required");
        Console.Write($"{title}: ");
        data = Console.ReadLine();
    }
}
```
This code request to the user to put the name on the console if the user only press enter the code keeps requesting data until the user put the name and press enter. here you don´t know when the code stops because the user can press 10 times enter or 100 or 1000 times until the name is written.

## Do while

The while loop tests the condition before executing the code following the while. The do ... while loop executes the code first, and then checks the condition. The do while loop is shown in the following code:

```cs
int counter = 0;
do
{
    Console.WriteLine($"Hello World!! {counter}");
    counter++;
} while (counter < 10);
```

## Break

Any kind of loop works with `break`, this reserved keyword is use to stop the loop at any moment for example 

```cs

int counter = 0;
while(true)
{
    if(counter>10)
    {
        /*
         This will stop the while loop 
         when is counter greather than 10
        */
        break;
    }
    counter++;
}
```