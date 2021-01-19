# Changing to MiniScaffold

- [ ] Get the latest Github version of your lib.

- [ ]  Create a clone in a different folder (as backup).

- [ ]  Remove all files and directories from your lib folder.

- [ ]  Run `dotnet new mini-scaffold` in your lib folder.

- [ ]  Update the `paket.dependencies` folder.


Add your own lib dependencies

- [ ] Update the `paket.reference` files with you own dependencies.

- [ ] Change the .net versions.


##### Lib proj

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>net5.0</TargetFrameworks>
  </PropertyGroup>
  <PropertyGroup>
    <Title>Informedica.Build.Template</Title>
    <Description>Informedica.Build.Template does the thing!</Description>

  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)'=='Release'">
    <Optimize>true</Optimize>
    <Tailcalls>true</Tailcalls>
    
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="AssemblyInfo.fs" />
    <Compile Include="Library.fs" />
  </ItemGroup>
  <Import Project="..\..\.paket\Paket.Restore.targets" />
</Project>
```

##### Test proj

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFrameworks>net5.0</TargetFrameworks>
        <GenerateProgramFile>false</GenerateProgramFile>
    </PropertyGroup>
    <ItemGroup>
        <ProjectReference Include="../../src/Informedica.Build.Template/Informedica.Build.Template.fsproj" />
    </ItemGroup>
        <ItemGroup>
        <Compile Include="AssemblyInfo.fs" />
        <Compile Include="Tests.fs" />
        <Compile Include="Main.fs" />
    </ItemGroup>
    <Import Project="..\..\.paket\Paket.Restore.targets" />
</Project>
```

Note that the `GenerateProgramFile<false>` is because when updating the test runners 
result in this issue: https://andrewlock.net/fixing-the-error-program-has-more-than-one-entry-point-defined-for-console-apps-containing-xunit-tests/

- [ ]  Change the `build.fsx`.


Disable the anayzers target. There was a [bug](https://github.com/ionide/FSharp.Analyzers.SDK/issues/22), but now something else goes wrong
with a null reference exception. 

```fsharp
//    ==> "FSharpAnalyzers"
```

You might also need to lower the `coverageThresholdPercent` to a lower setting.

- [ ] Update dependencies.

    dotnet tool restore
    dotnet paket update

- [ ] Fix the [problem](https://github.com/TheAngryByrd/MiniScaffold/issues/225) in the docsTool.

```fsharp
    let serveDocs refreshEvent docsDir =
        async {
            waitForPortInUse hostname port
            sprintf "http://%s:%d/index.html" hostname port |> openBrowser
        } |> Async.Start
        startWebserver refreshEvent docsDir (sprintf "http://%s:%d" hostname port)
```


- [ ] Move the content of the `RELEASE_NOTES.md` to the `CHANGELOG.md`

- [ ] Make sure that the `Assembly.info` files contain the right names and entries

- [ ] Use an opt-in approach in the `.gitignore` file.

You can check in Visual Studio in the folders view which files will be add to the repository.

- [ ] Run `/build.sh` or `build.cmd`.
