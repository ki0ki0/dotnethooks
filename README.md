# GitHooksFolderSetter

This project has only one goal, execute the following command: `git config core.hooksPath hooks` once. That way you could enforce policy on your project when executing basic Git commands.

For more information about git hooks please read [this article](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)

## Installation

Just install this package from VisualStudio UI, Package manager console, or with command line:

```sh
dotnet add package GitHooksFolderSetter
```
Custom hooks folder is set on first build action after package installation.

You can remove the `git-hook-folder.set` file in the `.git` folder to force the package to set the hooks folder once again.

You can customize the path of the hooks folder by specifying the `HooksPath` variable. You have to remove the `git-hook-folder.set` file if the package was installed before modification.

By default, the `HooksPath` variable is set to `hooks` which means the folder will be relative to the `.git` folder. For example :
```
- .git
- hooks/
  - commit-msg
- src/
  - MyProject/
    - MyProject.csproj
  - MyProject.sln
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <HooksPath>custom_hooks</HooksPath>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="GitHooksFolderSetter" Version="1.0.0" IncludeAssets="build" />
  </ItemGroup>

</Project>
```

## Acknowledgments

<https://github.com/Nagarian/dotnethooks>

<https://github.com/MrLuje/dotnet-format-hook>
