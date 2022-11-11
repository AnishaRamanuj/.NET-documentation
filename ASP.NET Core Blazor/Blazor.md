# Blazor #

Blazor WebAssembly is a **single-page app (SPA)** framework for building interactive client-side web apps with . NET. Blazor WebAssembly uses open web standards without plugins or recompiling code into other languages. Blazor WebAssembly works in all modern web browsers, including mobile browsers.

Blazor is a framework for building interactive client-side web UI with .NET:

* Create rich interactive UIs using C# instead of JavaScript.
* Share server-side and client-side app logic written in .NET.
* Render the UI as HTML and CSS for wide browser support, including mobile browsers.
* Integrate with modern hosting platforms, such as Docker.
* Build hybrid desktop and mobile apps with .NET and Blazor.

## Blazor Server ##

Blazor Server provides support for hosting Razor components on the server in an ASP.NET Core app. UI updates are handled over a SignalR connection.

The runtime stays on the server and handles:

* Executing the app's C# code.
* Sending UI events from the browser to the server.
* Applying UI updates to a rendered component that are sent back by the server.

The connection used by Blazor Server to communicate with the browser is also used to handle JavaScript interop calls.

Blazor Server apps render content differently than traditional models for rendering UI in ASP.NET Core apps using Razor views or Razor Pages. Both models use the Razor language to describe HTML content for rendering, but they significantly differ in how markup is rendered.

When a Razor Page or view is rendered, every line of Razor code emits HTML in text form. After rendering, the server disposes of the page or view instance, including any state that was produced. When another request for the page occurs, the entire page is rerendered to HTML again and sent to the client.


## JavaScript interop ##

For apps that require third-party JavaScript libraries and access to browser APIs, components interoperate with JavaScript. Components are capable of using any library or API that JavaScript is able to use. C# code can call into JavaScript code, and JavaScript code can call into C# code.
