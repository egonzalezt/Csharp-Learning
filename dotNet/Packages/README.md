# [Packages](https://docs.microsoft.com/en-us/learn/modules/dotnet-dependencies/2-dependency)

.NET commands

The .NET Core CLI has quite a few commands. The commands help you with tasks like installing packages, authoring packages, and initializing .NET projects. You don't need to know all the commands in detail. When you start out with .NET, you're likely to use only a subset of the commands. As you expand your use of .NET, you might use more and more commands from a variety of categories.

To help you remember what the commands do, it helps to think of them as belonging to categories:

Manage dependencies. Commands in this category cover installation, removal, cleaning up after package installations, and updating packages.

If you want a detailed list of all commands, enter `dotnet --help` in the terminal.

## How to install a package

Use the `dotnet add package <dependency name>` command to install a normal dependency that's meant to be used as part of your application.

### After installation

The installed packages are listed in the dependencies section of your .csproj file. If you want to see what packages are in the folder, you can enter `dotnet list package`

This command lists only the top-level packages and not dependencies of those packages that we call transitive packages. This is nice for a quick look. If you want a more in-depth view, you can list all transitive packages. When you do so, the list command looks like this one:

`dotnet list package --include-transitive`

## Restore dependencies

When you create or clone a project, **the included dependencies are not downloaded or installed until you build your project.** You can manually restore dependencies as well as project-specific tools that are specified in the project file by running the `dotnet restore` command. In most cases, you don't need to explicitly use the command. NuGet restore is run implicitly, if necessary, when you run commands like new, build, and run.

Clean up dependencies

Sooner or later, you're likely to realize that you no longer need a package. Or you might realize that the package you installed isn't the one you need. Maybe you've found one that will accomplish a task better. Whatever the reason, you should remove dependencies that you aren't using. Doing so keeps things clean. Also, dependencies take up space.

To remove a package from your project, you use the remove command like so: `dotnet remove package <name of dependency>`. This command will remove the package from the .csproj file for your project.

## [Versioning](https://docs.microsoft.com/en-us/learn/modules/dotnet-dependencies/4-dependency-management)

### Use semantic versioning

There's an industry standard called semantic versioning. **Semantic versioning is how you express the type of change that you or some other developer is introducing to a library**. Semantic versioning works by ensuring that a package has a version number and that the version number is divided into these sections:

* Major version. The leftmost number. For example, it's the 1 in 1.0.0. A change to this number means that you can expect breaking changes in code. You might need to rewrite part of your code.
* Minor version. The middle number. For example, it's the 2 in 1.2.0. A change to this number means that features have been added. Your code should still work. It's generally safe to accept the update.
* Patch version. The rightmost number. For example, it's the 3 in 1.2.3. A change to this number means that a change has been applied that fixes something in the code that should have worked. It should be safe to accept the update.

This table illustrates how the version number changes for each version type:

|Type	|What happens|
|----||----|
|Major version	|1.0.0 changes to 2.0.0|
|Minor version	|1.1.1 changes to 1.2.0|
|Patch version	|1.0.1 changes to 1.0.2|

| Type | What happens | 
|:------|:-----|
|Major version|1.0.0 changes to 2.0.0 |
|Minor version7|1.1.1 changes to 1.2.0|
|Patch versio|1.0.1 changes to 1.0.2|

## Find and update outdated packages

The `dotnet list package --outdated` command lists outdated packages. This command can help you learn when newer versions of packages are available. Here's a typical output from the command:

Output

| Top-level Package| Requested | Resolved | Latest | 
|:------|:-----|:------|:-----|
|Humanizer|2.7.*| 2.7.9 | 2.8.26 | 

Here are the meanings of the names of the columns in the output:

* Requested. The version or version range that you've specified.
* Resolved. The actual version that has been downloaded for the project that matches the specified version.
* Latest. The latest version available for update from NuGet.

The recommended workflow is to run these commands, in this order:

* Run `dotnet list package --outdated`. This command lists all the outdated packages. It provides information in the Requested, Resolved, and Latest columns.
* Run `dotnet add package <package name>`. If you run this command, it will try to update to the latest version. Optionally, you can pass in `--version=<version number/range>`.

### Some Usefull Commands

* dotnet list package
* dotnet list package --outdated
* dotnet list package --outdated --include-prerelease
* dotnet add package Humanizer
* dotnet add package Humanizer --version 2.11.10
* dotnet add package Humanizer --prerelease
