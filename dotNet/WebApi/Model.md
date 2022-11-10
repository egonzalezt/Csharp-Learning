# Model

The main idea of models is to represent objects or specify the structure of data that you may expect to process for example: 

```cs

namespace PersonsApi.Models
{
    public class Person
    {
        public int Number { get; set;}
        public string? Name { get; set; }
        public string? LastName { get; set; } = null!;  
        public string? Department { get; set; } = null!;  
        public DateTime BornDate { get; set; }
        public double Height { get; set; }
        public double Weight { get; set; }
    }
}
```

## Ways to represent models

On c# there are two ways to represent models to further use on the Api called **CLASS** and **RECORD**

```cs
namespace PersonsApi.Models
{
    public class Person
    {
        public int Number { get; set;}
        public string? Name { get; set; }
        public string? LastName { get; set; } = null!;  
        public string? Department { get; set; } = null!;  
        public DateTime BornDate { get; set; }
        public double Height { get; set; }
        public double Weight { get; set; }
    }
}

namespace PersonsApi.Models
{
    public record Person
    {
        public int Number { get; set;}
        public string? Name { get; set; }
        public string? LastName { get; set; } = null!;  
        public string? Department { get; set; } = null!;  
        public DateTime BornDate { get; set; }
        public double Height { get; set; }
        public double Weight { get; set; }
    }
}
```
At the beginning there is no such any difference between them because the struct is the same, so the main difference is the porpuse to use it.

The main purpose of record is to store data so it's not recommended to do another thing, also record are immutable, instead of class that data can mutate.

### When to use a record over a class?

Use a class if your object has unique logic. Classes are mutable so even if they have the same data, doesn't mean they are the same.

For example, if we think about a class that represents a window. Two windows on a house can look the same, have the same size and color, but they are not the same.

On the other hands, if we think of records as just bag of data, we only care about data being the same.

## [Model Validation](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/validation00)0

Similar to a database .Net provide to the developers some functionalities to handle errors or values

### Validation attributes

```cs
using System.ComponentModel.DataAnnotations;

namespace PersonsApi.Models
{
    public class Person
    {
        public int Number { get; set;}

        [Required]
        [StringLength(255)]
        [Display(Name = "Person Name")]
        public string? Name { get; set; }
        [Required]
        [StringLength(255)]
        [Display(Name = "Person LastName")]
        public string LastName { get; set; } = null!;  
        [Required]
        [StringLength(255)]
        [Display(Name = "Department")]
        public string Department { get; set; } = null!;  
        [Required]
        [DataType(DataType.Date)]
        [Display(Name = "Person BirthDate")]
        public DateTime BornDate { get; set; }
        [Required]
        [Range(0, 3.99)]
        public double Height { get; set; }
        [Required]
        [Range(0,500)]
        public double Weight { get; set; }
    }
}
```

Using this validation attributes you can handle the values that user put and return an error in the case of wrong values.

* `[StringLength(255)]` Maximum length of 255 chars.
* `[Required]` Value must be specified.
* `[DataType(DataType.Date)]` Value is required as DateType.
* `[Range(0,500)]` Only admits values between 0 - 500.
* `public string LastName { get; set; } = null!;` The `null!` is for Non-nullable.
* `public string? Name { get; set; }` The `?` is for Non-nullable.

#### [Other build-in attributes](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/validation?WT.mc_id=beginwebapis-c9-cephilli&view=aspnetcore-6.0#built-in-attributes)

* [ValidateNever]: Indicates that a property or parameter should be excluded from validation.
* [CreditCard]: Validates that the property has a credit card format.
* [Compare]: Validates that two properties in a model match.
* [EmailAddress]: Validates that the property has an email format.
* [Phone]: Validates that the property has a telephone number format.
* [Range]: Validates that the property value falls within a specified range.
* [RegularExpression]: Validates that the property value matches a specified regular expression.
* [Required]: Validates that the field isn't null.
* [StringLength]: Validates that a string property value doesn't exceed a specified length limit.
* [Url]: Validates that the property has a URL format.
* [Remote]: Validates input on the client by calling an action method on the server.

#### [Custom Validation](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/validation?WT.mc_id=beginwebapis-c9-cephilli&view=aspnetcore-6.0#custom-attributes)

```cs
public class ClassicMovieAttribute : ValidationAttribute
{
    public ClassicMovieAttribute(int year)
        => Year = year;

    public int Year { get; }

    public string GetErrorMessage() =>
        $"Classic movies must have a release year no later than {Year}.";

    protected override ValidationResult? IsValid(
        object? value, ValidationContext validationContext)
    {
        var movie = (Movie)validationContext.ObjectInstance;
        var releaseYear = ((DateTime)value!).Year;

        if (movie.Genre == Genre.Classic && releaseYear > Year)
        {
            return new ValidationResult(GetErrorMessage());
        }

        return ValidationResult.Success;
    }
}

// Model usage

public class Movie
{
    [ClassicMovie(1960)]
    [DataType(DataType.Date)]
    [Display(Name = "Release Date")]
    public DateTime ReleaseDate { get; set; }
}
```