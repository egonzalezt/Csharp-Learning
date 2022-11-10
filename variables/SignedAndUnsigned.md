# Signed and unsigned DataTypes

| Signed integral types| Unsigned integral types | 
|:------|:-----|
|**sbyte**: -128 to 127|**byte**: 0 to 255 |
|**short**: -32768 to 32767|**ushort**: 0 to 65535|
|**int**: -2147483648 to 2147483647|**uint**: 0 to 4294967295 |
|**long**: -9223372036854775808 to 9223372036854775807|**ulong**: 0 to 18446744073709551615|

## Signed integral Types

A signed type uses it's bytes to represent an **equal number of positive and negative numbers**. 

```cs
Console.WriteLine("Signed integral types:");
Console.WriteLine($"sbyte  : {sbyte.MinValue} to {sbyte.MaxValue}");
Console.WriteLine($"short  : {short.MinValue} to {short.MaxValue}");
Console.WriteLine($"int    : {int.MinValue} to {int.MaxValue}");
Console.WriteLine($"long   : {long.MinValue} to {long.MaxValue}");
```

* Signed integral types:
    * sbyte  : -128 to 127
    * short  : -32768 to 32767
    * int    : -2147483648 to 2147483647
    * long   : -9223372036854775808 to 9223372036854775807



## Unsigned integral types

An unsigned type uses its bytes to represent only positive numbers. 

```cs
Console.WriteLine("");
Console.WriteLine("Unsigned integral types:");

Console.WriteLine($"byte   : {byte.MinValue} to {byte.MaxValue}");
Console.WriteLine($"ushort : {ushort.MinValue} to {ushort.MaxValue}");
Console.WriteLine($"uint   : {uint.MinValue} to {uint.MaxValue}");
Console.WriteLine($"ulong  : {ulong.MinValue} to {ulong.MaxValue}");
```

* Unsigned integral types:
	* byte   : 0 to 255
	* ushort : 0 to 65535
	* uint   : 0 to 4294967295
	* ulong  : 0 to 18446744073709551615