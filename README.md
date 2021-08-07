# Create a Simple F# Application in Linux

1. [Install Dotnet](https://dotnet.microsoft.com/download)

2. Check Install
```bash
dotnet --version
```

3. Create Solution
```bash
dotnet new sln FSharpQuickStart
```

4. Create a Console Project
```bash
dotnet new console -lang "F#" -o src/FSharpQuickStart.Console
```
*You can search for templates*
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