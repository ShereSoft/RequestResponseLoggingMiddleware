# RequestResponseLoggingMiddleware
Middleware that provides HTTP request and response in plain string for logging purposes. Easy to use. Sync/Async support. No configuration is needed if used with ILogger&lt;T>. The logging middleware can also be configured or inherited for a custom logger. Extension methods are included for easy setup as well. No dependencies.

[![](https://img.shields.io/nuget/v/RequestResponseLoggingMiddleware.svg)](https://www.nuget.org/packages/RequestResponseLoggingMiddleware/)
[![](https://img.shields.io/nuget/dt/RequestResponseLoggingMiddleware)](https://www.nuget.org/packages/RequestResponseLoggingMiddleware/)

* Logs entire HTTP request and responses including headers.
* Requires zero configuration with ILogger<T> (default)
* Can be configured (via ctor with sync or async delegates) or inherited for more complex custom setup
* One line setup with extension methods (included)
* No library dependencies other than ASP.NET Core 3.1 Framework


#### Example
```csharp
public class Startup
{
    :
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        :
        app.UseRequestResponseLogging();  // logs to ILogger<T> by default
    }
}
```

#### With Custom Delegates
```csharp
public class Startup
{
    :
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        :
        app.UseRequestResponseLogging((c, r) => customLogger.LogInfo(r), (c, r) => customLogger.LogInfo(r));
    }
}
```

#### Async Delegates
```csharp
public class Startup
{
    :
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        :
        app.UseRequestResponseLogging(async (c, r) => await customLogger.LogInfoAsync(r), async (c, r) => await customLogger.LogInfoAsync(r));
    }
}
```

