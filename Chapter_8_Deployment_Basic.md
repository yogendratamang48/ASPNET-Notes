### 8. Deployment Basics 
#### IIS
IIS is request processing architecture which include  
* Windows Process Activation Service (WAS), which enables sites to use protocols other than HTTP and HTTPS
* A web server engine that can be customiezed by adding or removing modules
* Integrated request processing pipelines
### Deploying Web Application
Hosting .NET Core application requires following steps:
* publish an app to a folder on the hosting server (`dotnet publish` CLI tool can be used)
* Set up a process manager (IIS, nginx, Apache etc.) that starts the app when requests arrive and restarts the app after if crashes or the server reboots.
* Set up a reverse proxy that forwards requests to the app.
### References:
1. https://docs.microsoft.com/en-us/iis/get-started/introduction-to-iis/introduction-to-iis-architecture
2. https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/?tabs=aspnetcore2x