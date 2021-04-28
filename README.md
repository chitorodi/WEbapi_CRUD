# WEbapi_CRUD
Example for CRUD with  .NET

Prerequisites:
Visual Studio 2019 16.4 or later with the ASP.NET and web development workload

.NET Core 3.1 SDK or later



In this tutorial, you learn how to:

Create a web API project.
Add a model class and a database context.
Scaffold a controller with CRUD methods.
Configure routing, URL paths, and return values.
Call the web API with Postman.

API

GET /api/TodoItems


-----

From the File menu, select New > Project.
Select the ASP.NET Core Web Application template and click Next.
Name the project TodoApi and click Create.
In the Create a new ASP.NET Core Web Application dialog, confirm that .NET Core and ASP.NET Core 3.1 are selected. Select the API template and click Create.

Add a model class
A model is a set of classes that represent the data that the app manages. The model for this app is a single TodoItem class.

In Solution Explorer, right-click the project. Select Add > New Folder. Name the folder Models.

Right-click the Models folder and select Add > Class. Name the class TodoItem and select Add.

Replace the template code with the following code:

public class TodoItem
{
    public long Id { get; set; }
    public string Name { get; set; }
    public bool IsComplete { get; set; }
}


Add NuGet packages
From the Tools menu, select NuGet Package Manager > Manage NuGet Packages for Solution.
Select the Browse tab, and then enter Microsoft.EntityFrameworkCore.InMemory in the search box.
Select Microsoft.EntityFrameworkCore.InMemory in the left pane.
Select the Project check box in the right pane and then select Install.

Add the TodoContext database context
Right-click the Models folder and select Add > Class. Name the class TodoContext and click Add.

add the next code:

using Microsoft.EntityFrameworkCore;

namespace TodoApi.Models
{
    public class TodoContext : DbContext
    {
        public TodoContext(DbContextOptions<TodoContext> options)
            : base(options)
        {
        }

        public DbSet<TodoItem> TodoItems { get; set; }
    }
}

Get a list of to-do items
In the following code, an HTTP GET request is sent to the api/TodoItems route

fetch(uri)
  .then(response => response.json())
  .then(data => _displayItems(data))
  .catch(error => console.error('Unable to get items.', error));
  
  
