## How to create Visual Studio Multi Projects .Net Solution Template and deploy Nuget Package?

# How to create Visual Studio Multi Projects .Net Solution Template and deploy Nuget Package?


# Create Sample Project

To begin with, we create our sample project by going to the folder where we keep our repositories. I am using [dotnet CLI](https://docs.microsoft.com/tr-tr/dotnet/core/tools/) with powershell in Windows 10 but you can use different terminals and OS (MACOS, Linux etc.)

```
PS> mkdir Matech.Sample.Template 
PS> cd Matech.Sample.Template
```

Add some class library projects (Application, Domain, Infrastructure) and Web Api project.

```
PS Matech.Sample.Template> dotnet new classlib -n Application 
PS Matech.Sample.Template> dotnet new classlib -n Domain 
PS Matech.Sample.Template> dotnet new classlib -n Infrastructure 
PS Matech.Sample.Template> dotnet new webapi -n WebApi
```

Add Solution item

```
PS Matech.Sample.Template> dotnet new sln
```

Add multiple C# projects to a solution `Matech.Sample.Template.sln` using a globbing pattern (Windows PowerShell only):

```
PS Matech.Sample.Template> dotnet sln Matech.Sample.Template.sln add (ls -r **/*.csproj)
```

Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):

```
PS Matech.Sample.Template> dotnet sln Matech.Sample.Template.sln add **/*.csproj
```

You can check [dotnet sln](https://docs.microsoft.com/tr-tr/dotnet/core/tools/dotnet-sln).

# Matech.Sample.Template Project

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/758/0*wsGi9JkBf9x-TW6w.jpg" width="379" height="458" srcSet="https://miro.medium.com/max/552/0*wsGi9JkBf9x-TW6w.jpg 276w, https://miro.medium.com/max/758/0*wsGi9JkBf9x-TW6w.jpg 379w" sizes="379px"/></noscript>

Let’s go to t<span id="rmm"><span id="rmm">h</span></span>e folder where we created our project and add new classes to our project.

`Domain` will contain all entities, enums, exceptions, interfaces, types and logic specific to the domain layer. If you are interested in Clean Architecture, you can check my public open source [solution template for creating a ASP.NET Core Web Api following the principles of Clean Architecture](https://github.com/iayti/CleanArchitecture).

`Infrastructure` layer contains classes for accessing external resources such as file systems, web services, smtp, and so on. These classes should be based on interfaces defined within the application layer.

# Prerequisites for Database Migrations

*   If you don’t have [Entity Framework Core tools reference — .NET Core CLI](https://docs.microsoft.com/tr-tr/ef/core/miscellaneous/cli/dotnet), Install

```
PS Matech.Sample.Template> dotnet tool install --global dotnet-ef
```

Add Domain reference to Infrastructure project.

Add Application and Infrastructure reference to WebApi project.

Dependencies

*   Infrastructure
*   Microsoft.EntityFrameworkCore.SqlServer
*   Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore
*   WebApi
*   Microsoft.EntityFrameworkCore.Tools

Add initial create for database.

*   `--project Infrastructure` (optional if in this folder)
*   `--startup-project WebApi`
*   `--output-dir Migrations`

```
PS Matech.Sample.Template> dotnet ef migrations add --project Infrastructure --startup-project WebApi --output-dir Migrations
```

Sample template project is finally ready 😄

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1052/0*lhi0vgTEwG9kYRvB.jpg" width="526" height="801" srcSet="https://miro.medium.com/max/552/0*lhi0vgTEwG9kYRvB.jpg 276w, https://miro.medium.com/max/1052/0*lhi0vgTEwG9kYRvB.jpg 526w" sizes="526px"/></noscript>

# Adding .template.config and testing locally.

The example below demonstrates the file and folder structure of using a template.json to create a template pack. Check the [microsoft docs](https://docs.microsoft.com/en-us/dotnet/core/tools/custom-templates).

```
Matech.Sample.Template 
|___.template.config 
    |___template.json 
|___Application 
|___Domain 
|___Infrastructure 
|___WebApi 
|___Matech.Sample.Template.sln</span>
```

Configure your `template.json` and that's it 😄.

Let’s try our template locally.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/3208/0*qrTKPk956sruxuh2.jpg" width="1604" height="1042" srcSet="https://miro.medium.com/max/552/0*qrTKPk956sruxuh2.jpg 276w, https://miro.medium.com/max/1104/0*qrTKPk956sruxuh2.jpg 552w, https://miro.medium.com/max/1280/0*qrTKPk956sruxuh2.jpg 640w, https://miro.medium.com/max/1400/0*qrTKPk956sruxuh2.jpg 700w" sizes="700px"/></noscript>

Create a new project using our local template.

```
PS> mkdir Test_Local_Sample_Template 
PS> cd Test_Local_Sample_Template 
PS Test_Local_Sample_Template> dotnet new mst
```

Project was created 😄

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1246/0*7mpaaIN7k9jFchtK.jpg" width="623" height="197" srcSet="https://miro.medium.com/max/552/0*7mpaaIN7k9jFchtK.jpg 276w, https://miro.medium.com/max/1104/0*7mpaaIN7k9jFchtK.jpg 552w, https://miro.medium.com/max/1246/0*7mpaaIN7k9jFchtK.jpg 623w" sizes="623px"/></noscript>

Check the project and if anything is wrong, change the settings you made and install template locally for testing again.

Uninstall Template

```
PS> dotnet new --uninstall
PS> dotnet new -u <Project Folder Path>\Matech.Sample.Template
```

# Configure Nuget Deployment

First you need to create an account on [nuget.org](https://www.nuget.org/) like my profile [ilkerayti](https://www.nuget.org/profiles/ilkerayti).

# Download Nuget.exe and add to Path

Actually you don’t need to add path Nuget.exe but it is a very useful usage. [Download Nuget’s latest version.](https://www.nuget.org/downloads) Windows 10 search: Edit the system environment variables.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/708/0*ML_SkCaD6F0FMSIK.jpg" width="354" height="640" srcSet="https://miro.medium.com/max/552/0*ML_SkCaD6F0FMSIK.jpg 276w, https://miro.medium.com/max/708/0*ML_SkCaD6F0FMSIK.jpg 354w" sizes="354px"/></noscript>

Go to Environment Variables

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/824/0*5YS9uMx_EkJtXF33.jpg" width="412" height="474" srcSet="https://miro.medium.com/max/552/0*5YS9uMx_EkJtXF33.jpg 276w, https://miro.medium.com/max/824/0*5YS9uMx_EkJtXF33.jpg 412w" sizes="412px"/></noscript>

Go to System variables Path with double click.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1232/0*Z9qvVU7yeVYID0rY.jpg" width="616" height="575" srcSet="https://miro.medium.com/max/552/0*Z9qvVU7yeVYID0rY.jpg 276w, https://miro.medium.com/max/1104/0*Z9qvVU7yeVYID0rY.jpg 552w, https://miro.medium.com/max/1232/0*Z9qvVU7yeVYID0rY.jpg 616w" sizes="616px"/></noscript>

Add New nuget.exe file location in your system.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1030/0*2x9I9Yte5MjeaTpG.jpg" width="515" height="482" srcSet="https://miro.medium.com/max/552/0*2x9I9Yte5MjeaTpG.jpg 276w, https://miro.medium.com/max/1030/0*2x9I9Yte5MjeaTpG.jpg 515w" sizes="515px"/></noscript>

# Configure .nuspec file

Open terminal in your Matech.Sample.Template project folder

```
PS Matech.Sample.Template> nuget spec
```

Package.nuspec file must be created in your project folder.

After the configuration, we finally created a .nupkd file for nuget.org upload or push.

```
PS Matech.Sample.Template> nuget pack Package.nuspec -NoDefaultExcludes
```

If you don’t add nuget.exe to Environment System Variable Path just use the nuget.exe

```
PS Matech.Sample.Template> C:\Nuget\nuget.exe pack Package.nuspec -NoDefaultExcludes
```

Package was created.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1256/0*NsF82GWXQh5SvQiA.jpg" width="628" height="20" srcSet="https://miro.medium.com/max/552/0*NsF82GWXQh5SvQiA.jpg 276w, https://miro.medium.com/max/1104/0*NsF82GWXQh5SvQiA.jpg 552w, https://miro.medium.com/max/1256/0*NsF82GWXQh5SvQiA.jpg 628w" sizes="628px"/></noscript>

[Nuget Package Explorer](https://www.microsoft.com/en-us/p/nuget-package-explorer/9wzdncrdmdm3) is very useful tool for checking .nupkd file before publish.

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/1256/0*9lx0kHf4jsQdjlsQ.jpg" width="628" height="594" srcSet="https://miro.medium.com/max/552/0*9lx0kHf4jsQdjlsQ.jpg 276w, https://miro.medium.com/max/1104/0*9lx0kHf4jsQdjlsQ.jpg 552w, https://miro.medium.com/max/1256/0*9lx0kHf4jsQdjlsQ.jpg 628w" sizes="628px"/></noscript>

Finally we can upload to packages to Nuget servers 😄

Upload Package

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/2446/0*8Z7iETif7qEyj3xp.jpg" width="1223" height="1270" srcSet="https://miro.medium.com/max/552/0*8Z7iETif7qEyj3xp.jpg 276w, https://miro.medium.com/max/1104/0*8Z7iETif7qEyj3xp.jpg 552w, https://miro.medium.com/max/1280/0*8Z7iETif7qEyj3xp.jpg 640w, https://miro.medium.com/max/1400/0*8Z7iETif7qEyj3xp.jpg 700w" sizes="700px"/></noscript>

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/2446/0*wgkQArSguKluxd4B.jpg" width="1223" height="1270" srcSet="https://miro.medium.com/max/552/0*wgkQArSguKluxd4B.jpg 276w, https://miro.medium.com/max/1104/0*wgkQArSguKluxd4B.jpg 552w, https://miro.medium.com/max/1280/0*wgkQArSguKluxd4B.jpg 640w, https://miro.medium.com/max/1400/0*wgkQArSguKluxd4B.jpg 700w" sizes="700px"/></noscript>

<noscript><img alt="Image for post" class="ef dv dr je w" src="https://miro.medium.com/max/2368/0*Y40VzRLlk4ZuZqnL.jpg" width="1184" height="1173" srcSet="https://miro.medium.com/max/552/0*Y40VzRLlk4ZuZqnL.jpg 276w, https://miro.medium.com/max/1104/0*Y40VzRLlk4ZuZqnL.jpg 552w, https://miro.medium.com/max/1280/0*Y40VzRLlk4ZuZqnL.jpg 640w, https://miro.medium.com/max/1400/0*Y40VzRLlk4ZuZqnL.jpg 700w" sizes="700px"/></noscript>

Check [Matech.Sample.Template](https://www.nuget.org/packages/Matech.Sample.Template)

# Sample Template Usage

Open terminal in your repos folder.

```
PS> mkdir Your.Template.Name 
PS> cd Your.Template.Name
```

Template will use your folder name as project name

```
PS Your.Template.Name> dotnet new --install Matech.Sample.Template PS Your.Template.Name> dotnet new mst
```

# Support

If you are having problems, please let us know by [raising a new issue](https://github.com/iayti/Matech.Sample.Template/issues/new).

# License

This project is licensed with the [MIT license](https://github.com/iayti/Matech.Sample.Template/blob/master/LICENSE).

_Originally published at_ [_https://github.com/_iayti/Matech.Sample.Template](https://github.com/iayti/Matech.Sample.Template)_._