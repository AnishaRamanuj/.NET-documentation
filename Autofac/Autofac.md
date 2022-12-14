## What Is Autofac? ##

Autofac is an inversion of control (IoC) container.  If you’re not familiar with this idea, it’s a way in the object-oriented world to inject class dependencies (usually into a constructor).

If you are not familiar with this idea in the object-oriented world, it is a way of injecting dependencies that are relied upon by other classes usually in a constructor. Autofac has the reputation of being the most widely used framework in the .NET community. It is one of the most downloaded packages among developers. AutoFac provides better integration for the ASP.NET MVC framework and is developed using Google code.

Autofac is an IoC container for Microsoft .NET. It manages the dependencies between classes so that applications stay easy to change as they grow in size and complexity. This is achieved by treating regular .NET classes as components.

Emphasis theirs.

So Autofac provides you with easy inversion of control, with the idea that this will keep your dependencies manageable and your code clean as it grows.  Interesting, given its good percentile scores in my research.

## Okay, so Why Study Autofac? ##

Autofac exists to make your code testable, clean, and decoupled.  So seeing its initial stats at a quick glance made me wonder, “is Autofac’s code testable, clean, and decoupled?”  Its scores for testability and readability seem to indicate that yes, it is.  But we can certainly dive a lot deeper.

## Autofac, What’s the Verdict? ##

Looking inward at an IoC framework, we see that it does indeed keep its own type coupling to a minimum and that it writes testable code and then tests that code.  At the namespace level, things get a little iffy.  But that’s really the only complaint.

If I went and fixed the namespace issues, the codebase would be right on the precipice of having an “A” rating for technical debt.  (I know this because I disabled the namespace-related warnings and observed the debt rating).  This means that Autofac, on the whole, has few warnings across the board, particularly of high severity.  NDepend thinks this is a good codebase and my ranking of codebases agrees.

So there you have it.  A codebase aimed at helping other people keep their code tidy, testable, and decoupled is, itself, a pleasure to edit and to work in.

## Getting Started ##
The basic pattern for integrating Autofac into your application is:

- Structure your app with inversion of control (IoC) in mind.

- Add Autofac references.

- At application startup…

    - Create a ContainerBuilder.

    - Register components.

    - Build the container and store it for later use.

- During application execution…

    - Create a lifetime scope from the container.

    - Use the lifetime scope to resolve instances of the components.

## You could address that type in one of two ways: ##

As the type itself, **_SomeType_**

As the interface, an **_IService_**

In this case, the component is SomeType and the services it exposes are SomeType and IService.
```
public class SomeType : IService
{
}
```

In Autofac, you’d register that with a **_ContainerBuilder_**
```
// Create your builder.
var builder = new ContainerBuilder();

// Usually you're only interested in exposing the type
// via its interface:
builder.RegisterType<SomeType>().As<IService>();

// However, if you want BOTH services (not as common)
// you can say so:
builder.RegisterType<SomeType>().AsSelf().As<IService>();
```
## Application Execution ##
During application execution, you’ll need to make use of the components you registered. You do this by resolving them from a lifetime scope.

The container itself is a lifetime scope, and you can technically just resolve things right from the container. It is not recommended to resolve from the container directly, however.

However, the container lives for the lifetime of your application. If you resolve a lot of stuff directly from the container, you may end up with a lot of things hanging around waiting to be disposed. That’s not good (and you may see a “memory leak” doing that).

Instead, create a child lifetime scope from the container and resolve from that. When you’re done resolving components, dispose of the child scope and everything gets cleaned up for you.
