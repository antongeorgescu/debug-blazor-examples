# How to debug Blazor WebAssembly applications

### Instructions
Watch the YouTube video at https://www.youtube.com/watch?v=QgRwaw_RQ8w

### Prerequisites
The required libraries and their versions are be found in <client_blazor>.csproj file, that has the following content:

&nbsp;&nbsp;&lt;Project Sdk="Microsoft.NET.Sdk.Web"&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;PropertyGroup&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;TargetFramework&gt;netstandard2.1&lt;/TargetFramework&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RazorLangVersion&gt;3.0&lt;/RazorLangVersion&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/PropertyGroup&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;ItemGroup&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="3.2.1" /&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.Build" Version="3.2.1" PrivateAssets="all" /&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="3.2.1" PrivateAssets="all" /&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.2.0-preview3.20168.3" /&gt;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/ItemGroup&gt;<br/>
&nbsp;&nbsp;&lt;/Project&gt;<br/>

### Debug in Chrome browser - Open Chrome debugger
* Type "dotnet run" in VS Code cmd terminal
* Type "CTRL-F5" (run without debugging in chrome)
* Select Environment "Blazor WebAssembly Debug"
* Select "Win-R" and type chrome --remote-debugging-port=9222 --user-data-dir="C:\Users\ag4488\AppData\Local\Temp\blazor-chrome-debug" --no-first-run http://localhost:5000/counter
* Focus on browser page under localhost:5000 and click Shift-Alt-D(el)
* Expand file:// folder, select the .razor file and add the brakepoints you want

##### Alternate paths for opening the Chrome debugger
* chrome --remote-debugging-port=9222 --user-data-dir="C:\Users\ag4488\AppData\Local\Temp\blazor-chrome-debug" http://localhost:5000/counter --no-first-run --disable-web-security --enable-logging=stderr --v=1 log.txt 2>&1
* chrome --remote-debugging-port=9222 --user-data-dir="C:\Users\ag4488\AppData\Local\Temp\blazor-chrome-debug" http://localhost:5000/counter --no-first-run --disable-web-security --enable-logging=stderr --v=1 --ignore-certificate-errors
* chrome --remote-debugging-port=9222 --user-data-dir="C:\Users\ag4488\AppData\Local\Temp\blazor-chrome-debug" http://localhost:33644 --no-first-run --disable-web-security --enable-logging=stderr --v=1 --ignore-certificate-errors

### Debug in Visual Studio 2019 or Visual Studio Code
The current repository keeps the two kinds of Blazor WebAssembly implementation: client and server hosted.<br/>
Take the launch.json files under .vscode folders in the respective projects, customize them to meet your specific needs and then deploy them in your projects 
