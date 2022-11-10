# Implicitly typed local variables

As a good practice C# defines Implicitly typed local variables with can detect automatically with datatype the user is trying to store.

## What are implicitly typed local variables?

An implicitly typed local variable is created using the `var` keyword, which instructs the C# compiler to infer the type.

for example
```cs
var nickname = "egonzalezt";
```

but take care using these type of declaration because people whom know about JavaScript know that these is possible 

```js 
var nickname = "egonzalezt";
nickname = [1,2,3,4,5,6,7,8,9,10];
```

If you try to do that on C# the compiler return an error because when the variable is declared and assigned with some data type that variable only store that data type.

Also it's important to initialize the Implicitly local variable to avoid errors this is required because C# need to know which data type the user is trying to store 

`(1,5): error CS0818: Implicitly-typed variables must be initialized`

## Good Practice

Using implicitly local variables is a good practice to write more understandable code and also to avoid the repetition of keywords when is too obvious the type that the programmer is storing 

```cs

/*
 Don't use it 
 on the right hand side it's implicitly declared a decimal data type.
*/

decimal xCoordinate = 120.1234564m; 

/*
 Use it 
 on the right hand side it's implicitly declared a decimal data type,
 so it's no needed to specify on the left hand side the type.
*/

var xCoordinate = 120.1234564m; 

/*
 Don't use it 
 the variable is storing data that will be returned by a method,
 but sometimes it doesn't know which data type is.
 for that reason is requred to specity the data type
*/

var foo = bar();

//better use

decimal foo = bar();

```