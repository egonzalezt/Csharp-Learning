# [Api Controller](https://docs.microsoft.com/en-us/learn/modules/build-web-api-aspnet-core/4-aspnet-controllers)

A controller is a public class with one or more public methods known as actions. By convention, a controller is placed in the project root's Controllers directory. **The actions are exposed as HTTP endpoints via routing.** So an HTTP GET request to https://localhost:{PORT}/weatherforecast causes the Get() method of the WeatherForecastController class to be executed.

The first thing to notice is that this class inherits from the ControllerBase base class. This base class provides a lot of standard functionality for handling HTTP requests.

[ApiController attribute](https://docs.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-6.0#apicontroller-attribute)

Route defines the routing pattern for example `https://localhost:{PORT}/clients/payments/history`

```cs
[ApiController]
[Route("[controller]")]
public class WeatherForecastController : ControllerBase
```

Controllers is the entry point of the request where you can process or handle what need to do with that data.


## [How to define an entry point](https://docs.microsoft.com/en-us/learn/modules/build-web-api-aspnet-core/6-exercise-add-controller)

```cs
namespace PersonsApi.Controllers;

[ApiController]
[Route("[controller]")]
public class PersonController : ControllerBase
{
    public PersonController()
    {
    }

    // GET all action
    [HttpGet]
    public ActionResult<List<Person>> GetAll() => PersonService.GetAllPersons();

    // GET by Id action
    [HttpGet("{id}")]
    public ActionResult<Person> Get(int id)
    {

    }

    // POST action
    [HttpGet]
    public IActionResult Create(Person person)
    {

    }

    // DELETE action
    [HttpDelete("{id}")]
    public IActionResult Delete(int id)
    {

    }

}
```

`[Http<Method>]` has different types depending on the operation that the user or program needs to do 
* [HttpGet]
* [HttpPost]
* [HttpDelete]
* [HttpPut]
* [HttpPatch]

[HttpGet] describes that user will return or get data but this method is overloaded so also can be use as:
* `[HttpGet("{id}")]` get method with querystring.
* `[HttpGet("getallpersons/{id}")]` get method with custom route and query string.

also this overload methods on `[HttpGet]` can also use by the others like Delete or Put.

## [ActionResult](https://docs.microsoft.com/en-us/aspnet/core/web-api/action-return-types?view=aspnetcore-6.0#iactionresult-type)

On the previous example you see `ActionResult` on different methods 

```cs
[HttpGet("{id}")]
public ActionResult<Person> Get(int id)
{
}
```

**Action Result is actually a data type**. When it is used with action method, it is called return type. As you know, an action is referred to as a method of the controller, **the Action Result is the result of action when it executes. In fact, Action Result is a return type. This return type has many other derived types.**

Action Result is use to return any HTTP status code like 201 or 404 with generic information [Methods](https://docs.microsoft.com/en-us/dotnet/api/system.web.http.apicontroller.badrequest).

for example on the get request `ActionResult<Person>` specify that the action get will return a person or a set of persons `ActionResult<List<Person>>`

## [IActionResult](https://docs.microsoft.com/en-us/aspnet/core/web-api/action-return-types?0#iactionresult-type)

The IActionResult return type is appropriate when multiple ActionResult return types are possible in an action. The ActionResult types represent various HTTP status codes. **Any non-abstract class deriving from ActionResult qualifies as a valid return type.**

for example if a person is deleted it can return the id of the person or a record or json but when the person doesn't exist it will be returned an error so the content may vary
```cs
    // DELETE action
    [HttpDelete("{id}")]
    public IActionResult Delete(int id)
    {
        var person = PersonService.FindPersonById(id);

        if (person is null)
            return NotFound();

        PersonService.Delete(id);

        return NoContent();
    }
```

## [IEnumerable](https://docs.microsoft.com/en-us/dotnet/api/system.collections.ienumerable)

Many times there is a need to loop through a collection of classes or lists which are anonymous types, **IEnumerable interface is a generic interface which allows looping over generic or non-generic lists.**

```cs
public IEnumerable<Person> GetAll() => PersonService.Persons;
```

with IEnumerable it is only required the data type that is going to be iterated `IEnumerable<Person>` then return to IEnumerable the list to loop `PersonService.Persons;`