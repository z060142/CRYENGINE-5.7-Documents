# Using Console Command

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26875202
- Page ID: 26875202
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > Using Console Command
- Parent: C# Programming

## Content

## Creating Console Commands

A Console Command in C# is a delegate type with the following signature:

```
public delegate void ManagedConsoleCommandFunctionDelegate(params string[] arguments);
```

There are two ways to create console commands in C#:

- Applying C# Attributes
- Manual registration and deregistration

### Applying C# Attributes

A Console Command can be realized by applying a C# attribute to any static function. An example is shown below:

```
[ConsoleCommand("AConsoleCommand", (uint)EVarFlags.VF_DEV_ONLY, "This is a Console Command from CSharp" )]
static void AConsoleCommand(string[] arguments)
{
// other code
}
```

On successful execution of a Console Command, the arguments will be passed back as arguments in a string array (including the command name)

ConsoleCommand attribute applied to non-static functions will be ignored. For non-static functions, please use manual registration as shown below.

### Manual Registration and Deregistration

Console Commands can also be created by function call. This is the only way to create a console command in non-static functions. To register a Console Command function, use the following function:

```
ConsoleCommand.RegisterManagedConsoleCommandFunction(string commandName, uint nFlags, string commandHelpText, ManagedConsoleCommandFunctionDelegate consoleCmd Delegate)
```

To unregister a Console Command function, use the following function:

```
ConsoleCommand.UnregisterManagedConsoleCommandFunction(string commandName)
```

### Validating Console Commands

Console Commands are validated with the ConsoleCommandAttributeManager. The validation of Console Command attributes will be activated if a "***DEBUG***" attribute is declared in the code. If nonstatic functions are applied with the ConsoleCommand attribute, a ** ConsoleVariableConfigurationException** exception will be thrown.
