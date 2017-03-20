# Kentico Cloud .NET MVC Boilerplate
[![Build status](https://ci.appveyor.com/api/projects/status/1s02tbk1tml2wdmj/branch/master?svg=true)](https://ci.appveyor.com/project/kentico/cloud-boilerplate-net/branch/master)
[![NuGet](https://img.shields.io/nuget/v/KenticoCloud.CloudBoilerplateNet.svg)](https://www.nuget.org/packages/KenticoCloud.CloudBoilerplateNet/)

This boilerplate includes a set of features and best practices to kick off your website development with Kentico Cloud smoothly.

## What's included

- Kentico Delivery SDK
- Setup for Dev and Production environment
- Unit tests ([xUnit](https://xunit.github.io))
- Error handling (404, 500, ...)
- 301 URL Rewriting
- Logging

## Quick start

### Installation from NuGet

1. You must have the latest version of the dotnet tooling installed. It comes with Visual Studio 2017 or you can download with the [.NET Core SDK](https://www.microsoft.com/net/download/core).
2. Open Developer Command Prompt for VS 2017
3. Run `dotnet new --install KenticoCloud.CloudBoilerplateNet::*` to install the boilerplate to your machine
4. Run `dotnew new cloud-boilerplate-net --name "MyWebsite"  [--output "<path>"]`
5. Open in Visual Studio 2017/Code and Run

### Installation from source
TODO

## How to's


### How to change Kentico Cloud Project Id and Delivery Preview API key

Kentico Cloud Project Id is stored inside `appsettings.json` file. This setting is automatically loaded [using Options and configuration objects](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration). You can also provide additional environment specific configuration in `appsettings.production.json` and `appsettings.development.json` files.

For security reasons, Delivery Preview API key should be stored outside of the project tree. It's recommended to use [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets) to store sensitive data.


### How to generate Strongly Typed Models for Content Types

Content Type Models are generated by [models generator utility](https://github.com/Kentico/cloud-generators-net). By convention, all Content Type Models are stored within the `Models/ContentTypes` folder. All generated classes are partial, that means, you can extend the model with custom methods in a separate file. Do not modify generated models, they can be regenerated and your changes will be lost.


### How to handle 404 errors or any other error

Error handling is setup by default. Any server exception or error response within 400-600 status code range is handled by ErrorController. By default, it's configured to display Not Found error page for 404 error and General Error for anything else. 


### How to handle 301 Permanent redirect


The Boilerplate is configured to load all [URL Rewriting](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/url-rewriting) rules from [IISUrlRewrite.xml](/src/CloudBoilerplateNet/IISUrlRewrite.xml) file. Add or modify existing rules to match your expected behavior.

:warning: ASP.NET Core 1.1 currently [doesn't support Rewrite Maps](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/url-rewriting#unsupported-features), but there is a simple workaround for `/oldUrl -> /newUrl` mapping (see [IISUrlRewrite.xml](/src/CloudBoilerplateNet/IISUrlRewrite.xml) for example).


## Feedback & Contributing
Any feedback is much appreciated. Check out the [contributing](https://github.com/Kentico/Home/blob/master/CONTRIBUTING.md) to see the best places to file issues, start discussions and begin contributing.
