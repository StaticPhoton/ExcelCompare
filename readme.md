The 'FUNCTIONS_WORKER_RUNTIME' is set to 'dotnet-isolated', which does not match the worker runtime metadata found in the deployed function app artifacts. The deployed artifacts are for 'dotnet'. See https://aka.ms/functions-invalid-worker-runtime for more information. The application will continue to run, but may throw an exception in the future.

----

A C# Azure Function application, target framework .NET 8.0. Service A is registered as a dependency. A has dependency on another service, Service B. Service B is not registered as a dependency.

In .NET 6, this did not cause an issue. The constructor of Service A will receive a null parameter in its constructor in place of an instance of Service B. The constructor can check if it's null and decide what to do.

But, in .NET 8, Service A won't be created. It will throw an exception, saying it could not resolve dependency Service B.

What's the reason for this difference? When and why was this change introduced?
