# Create a Simple F# Application in Linux

## Setup Project

1. [Install Dotnet](https://dotnet.microsoft.com/download)

2. Check Install

```bash
dotnet --version
```

3. Create Solution

```bash
dotnet new sln --name FSharpQuickStart
```

4. Create a Console Project

```bash
dotnet new console -lang "F#" -o src/FSharpQuickStart.Console
```

You can also search for templates

```bash
# Display Locally Available Templates
dotnet new --list

# Search Online
dotnet new <Search Text> --search
```

5. Create a Test Project

```bash
dotnet new nunit -lang "F#" -o tests/FSharpQuickStart.Tests
```

6. Add Projects to Solution

```bash
dotnet sln add src/FSharpQuickStart.Console
dotnet sln add tests/FSharpQuickStart.Tests
```

7. Add Reference to Console Project to Test Project

```bash
dotnet add tests/FSharpQuickStart.Tests reference src/FSharpQuickStart.Console
```

## Add/Remove Files From Projects

1. Add/Remove the .fs File in Your Project Folder

2. Add/Remove the File Reference in the Project File

This is an example from the [Test Project](./tests/FSharpQuickStart.Tests/FSharpQuickStart.Tests.fsproj)

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>

    <IsPackable>false</IsPackable>
    <GenerateProgramFile>false</GenerateProgramFile>
  </PropertyGroup>

  <ItemGroup>
    <!-- NOTE THE FSHARP COMPILER WILL LOOK AT THESE FILES IN ORDER -->
    <!-- FOR EXAMPLE IF YOU HAVE A FUNCTION FROM UnitTest1.fs USED IN Program.fs  -->
    <!-- THEN IT MUST COME AFTER LIKE SO -->
    <Compile Include="UnitTest1.fs" />
    <Compile Include="Program.fs" />
    <!-- To Add MyFile.fs -->
    <Compile Include="MyFile.fs" />
    <!-- To Remove the complie tags with files you want to delete -->
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.9.4" />
    <PackageReference Include="NUnit" Version="3.13.1" />
    <PackageReference Include="NUnit3TestAdapter" Version="3.17.0" />
    <PackageReference Include="coverlet.collector" Version="3.0.2" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\..\src\FSharpQuickStart.Console\FSharpQuickStart.Console.fsproj" />
  </ItemGroup>

</Project>
```

## Running Solution

- Run Console Project

```bash
dotnet run --project src/FSharpQuickStart.Console/
```

- Run Tests

```bash
dotnet test
```

## Adding a Nuget Package

1. Search for Nuget at the [here](https://www.nuget.org/)

2. Add Nuget Package to a Project

```bash
dotnet add src/FSharpQuickStart.Console package Newtonsoft.Json
```
