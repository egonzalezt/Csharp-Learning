# RestAPI

Representational State Transfer (REST) is an architectural style for building web services. REST requests are made over HTTP. They use the same HTTP verbs that web browsers use to retrieve webpages and to send data to servers. The verbs are:

* **GET:** Retrieve data from the web service.
* **POST:** Create a new item of data on the web service.
* **PUT:** Update an item of data on the web service.
* **PATCH:** Update an item of data on the web service by describing a set of instructions about how the item should be modified. The sample application in this module doesn't use this verb.
* **DELETE:** Delete an item of data on the web service.

## [Create an API using CLI](https://docs.microsoft.com/en-us/learn/modules/build-web-api-aspnet-core/3-exercise-create-web-api)

to create an api you need to run this command on your command line interface but be ensure that you already have install dot net sdk `dotnet new webapi -f net6.0`

By default .net Apis has enabled Swagger to test and undestand the endpoints also you can use .NET HTTP REPL to test your Api (like a kind of postman).

Also see [Create web APIs with ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-6.0) and [Beginner's Series to: Web APIs](https://docs.microsoft.com/en-us/shows/Beginners-Series-to-Web-APIs/)