# JavaScriptServices

This project is part of ASP.NET Core. You can find samples, documentation and getting started instructions for ASP.NET Core at the [Home](https://github.com/aspnet/home) repo.

## What is this?

`JavaScriptServices` is a set of technologies for ASP.NET Core developers whose applications involve JavaScript. It's especially useful if you use Angular 2 / React / Knockout / etc. on the client, or if you build your client-side resources using Webpack.

These technologies consist of:

 * A set of NuGet/NPM packages that implement the functionality
 * A Yeoman generator that creates preconfigured app starting points
 * Samples

Everything here is cross-platform, and works with .NET Core 1.0 RC2 or later on Windows, Linux, or OS X.

## Creating new applications

If you want to build a brand-new ASP.NET Core app that uses Angular 2 / React / Knockout on the client, consider starting with the `aspnetcore-spa` generator. This lets you choose your client-side framework, and generates a starting point that includes applicable features such as Webpack dev middleware, server-side prerendering, and efficient production builds. It's much easier than configuring everything to work together manually.

See: [getting started with the `aspnetcore-spa` generator](http://blog.stevensanderson.com/2016/05/02/angular2-react-knockout-apps-on-aspnet-core/).

## Adding to existing applications

If you have an existing ASP.NET Core application, or if you just want to use the underlying JavaScriptServices packages directly, you can install these packages using NuGet and NPM:

 * `Microsoft.AspNetCore.NodeServices`
   * This provides a fast and robust way for .NET code to run JavaScript on the server inside a Node.js runtime.
   * Most applications developers don't need to use this directly, but you can do so if you want to implement your own functionality that involves calling Node.js code from .NET at runtime.
   * Find [documentation and usage examples here](https://github.com/aspnet/JavaScriptServices/tree/master/src/Microsoft.AspNetCore.NodeServices#microsoftaspnetcorenodeservices).
 * `Microsoft.AspNetCore.SpaServices`
   * This provides infrastructure that's generally useful when building Single Page Applications (SPAs) with technologies such as Angular 2 or React (such as server-side prerendering and webpack middleware). Internally, it uses the `NodeServices` package to implement its features.
   * Find [documentation and usage examples here](https://github.com/aspnet/JavaScriptServices/tree/master/src/Microsoft.AspNetCore.SpaServices#microsoftaspnetcorespaservices).
 * `Microsoft.AspNetCore.AngularServices`
   * This builds on the `SpaServices` package and includes features specific to Angular 2. Currently, this includes validation helpers and a *cache priming* feature, which let you pre-evaluate ajax requests on the server so that client-side code doesn't need to make network calls once it's loaded.
   * The code is [here](https://github.com/aspnet/JavaScriptServices/tree/master/src/Microsoft.AspNetCore.AngularServices), and you'll find a usage example for [the validation helper here](https://github.com/aspnet/JavaScriptServices/blob/master/samples/angular/MusicStore/wwwroot/ng-app/components/admin/album-edit/album-edit.ts), and for the [cache priming here](https://github.com/aspnet/JavaScriptServices/blob/master/samples/angular/MusicStore/Views/Home/Index.cshtml#L7-8). Full docs are to be written.

At some point, if we have React-specific features, they will go into a package called `Microsoft.AspNetCore.ReactServices`. Presently there's no need for any such package, because the functionality we want is already included in `SpaServices` without having to be specific to React. Nothing extra is currently needed.

If you want to build a helper library for some other SPA framework, you can do so by taking a dependency on `Microsoft.AspNetCore.SpaServices` and wrapping its functionality in whatever way is most useful for your SPA framework.

## Samples and templates

Inside this repo, the `templates` directory contains the application starting points that the `aspnetcore-spa` generator emits. If you want, you can clone this repo and run those applications directly. But it's easier to [use the Yeoman tool to run the generator](http://blog.stevensanderson.com/2016/05/02/angular2-react-knockout-apps-on-aspnet-core/).

Also in this repo, the `samples` directory contains examples of using the JavaScript services family of packages with Angular 2 and React, plus examples of standalone `NodeServices` usage for runtime code transpilation and image processing.

**To run the samples:**

 * Clone this repo
 * Change directory to the same you want to run (e.g., `cd samples/angular/MusicStore`)
 * Restore dependencies (run `dotnet restore` and `npm install`)
 * Run the application (`dotnet run`)
 * Browse to [http://localhost:5000](http://localhost:5000)

## Contributing

If you're interested in contributing to the various packages, samples, and project templates in this repo, that's great! You can run the code in this repo just by:

 * Cloning the repo
 * Running `dotnet restore` at the repo root dir
 * Going to whatever sample or template you want to run (e.g., `cd templates/Angular2Spa`)
 * Restoring NPM dependencies (run `npm install`)
 * Launching it (`dotnet run`)

If you're planning to submit a pull request, and if it's more than a trivial fix (e.g., for a typo), it's usually a good idea first to file an issue describing what you're proposing to do and how it will work. Then you can find out if it's likely that such a pull request will be accepted, and how it fits into wider ongoing plans.
