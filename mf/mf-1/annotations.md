# Annotations

### @Command <a id="command"></a>

This annotation can only be used on the command class. It tells **MF** what command to register on. It also requires a string, which in this case will be the command name. For example for `/command`.

```java
@Command("command")
```

### @Alias <a id="alias"></a>

This annotation will create an alias for your commands and subcommands. This can be used for both the command class and the subcommand method.  
You can set one or more aliases.

```java
// For one alias only.
@Alias("aliascommand")

// Multiple
@Alias({"firstalias", "secondalias"})
```

### @Default <a id="default"></a>

This annotation can only be used in a method, and it's used to set a default command. This will be the command that is run without a subcommand.  
For example, if you want many commands like `/command one` and your help command to not have a subcommand like `/command`, you set it as default.

```java
@Default
```

### @SubCommand <a id="subcommand"></a>

This annotation can only be used in a method and it's used to set a subcommand.  
For example, to set the command `/command one` the _one_ is the subcommand.

```java
@SubCommand("one")
```

### @Completion <a id="completion"></a>

This annotation can be both used on the method or on the parameter of a method.  
It is used to generate a tab completion for your commands.  
Examples:

```java
// Let's complete the first argument with a player name and the second with a number from 1 to 20.

// For completion on a method 
@Completion({"#players", "#range:1-20"})
public void commandTest(final CommandSender sender, final Player player, final Integer number)

// For completion on a parameter
public void commandTest(final CommandSender sender, @Completion("#players") final Player player, @Completion("#range:1-20") Integer number)
```

### @CompleteFor <a id="permission"></a>

This annotation will give you the freedom to handle the tab completion the way you want.  
To use it, make a new method on your command class that returns a `List<String>` then use the annotation to point it to the sub command you want to handle for.   
For completing a sub command annotated with `@Default` use `"default"` as the target.  
Follow the example under:

```java
@CompletionFor("subcommand")
public List<String> commandCompletion(final CommandSender commandSender, final List<String> completionArguments) {
    // Handle the tab completion for the Sub Command "test" here.
    
    return new ArrayList<>();
}
```

### @Permission <a id="permission"></a>

This annotation can only be used in a method and it sets the which permission node is required to run the command.

```java
// Single permission
@Permission("plugin.command")

// Multiple permissions
@Permission({"plugin.command.one", "plugin.command.two"})
```

### @WrongUsage <a id="optional"></a>

This annotation will display the correct syntax of your command when the player types in the wrong usage.  
You can use raw text in it or register a custom message using the [MessageHandler](messages.md#wrong-usage) and use it's `ID`.  
If the message `ID` is not registered it'll simply display the `ID` to the player.

```java
// Raw message
@WrongUsage("&c/cmd test <text>")

// Using 
@WrongUsage("#cmd-syntax")
```

### @Optional <a id="optional"></a>

This annotation can only be used on parameters and only on the last parameter. This will make it so the last argument is optional. If the player does not type the last argument it'll return `null`.  
_**ATENTION**_ ****- Because of returning `null` primitive data types will not work, for example instead of `int` use `Integer`, for optional parameters only though!

```java
public void commandTest(final CommandSender sender, final String firstArgument, @Optional final String optionalArgument)
```

### @Values

This annotation will work similar to the `@Completion` annotation, however it can only be used in the parameter. The difference of using Values instead of Completion is that it'll be checked and the only values allowed for that argument. For example if you set a tab completion to only have the Materials `STONE` and `DIAMOND` even if `OAK_WOOD` is a valid Material it'll return `null`as it is not part of the tab completion.

```java
public void commandTest(final CommandSender sender, @Values("#some") final Material materia)
```

