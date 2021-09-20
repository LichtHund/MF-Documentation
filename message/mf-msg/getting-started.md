# Getting started

## Message

To get started first you need to create a `BukkitMessage`.

```java
final BukkitMessage message = BukkitMessage.create();
```

This will be the base of every message you parse.

## Message Options

You can also specify some message options to the message creator, this allows you to control how the message will be parsed.

The base of the message options is the `MessageOptions` builder:

```java
MessageOptions.builder();
```

With it you can remove some formats:

```java
final MessageOptions messageOptions = MessageOptions.builder().removeFormat(Format.BOLD).build();
```

In this example, the BOLD format will be removed and it'll not parse the bold portion of the message.

You can also set a default color to be used in the messages:

```java
final MessageOptions messageOptions = MessageOptions.builder().setDefaultColor(new FlatColor("#38ef7d")).build();
```

Available color types are

* **FlatColor** - Takes in a String with a color, can be hex or just the name, for example: `FlatColor("red");`
* **GradientColor** - Takes in a List of `Color` objects.
* **RainbowColor** - Takes two values, a saturation level and a brightness level.

Finally you can pass the format options to the message creator:

```java
final BukkitMessage message = Message.create(messageOptions);
```

## Parsing

Finally all there is left to do is parsing the message:

```java
final MessageComponent component = message.parse("**Hello** __everyone__!");
```

The `MessageComponent` holds the parsed values that you can use for anything you want.

```java
// Sends JSON message
component.sendMessage(player);

component.sendActionBar(player, fadeIn, stay, fadeOut);
component.sendSubTitle(player, fadeIn, stay, fadeOut);
component.sendTitle(player, fadeIn, stay, fadeOut);

// Parsed String to use in items, etc
final String parsed = component.toString();
// Raw JSON String
final String json = component.toJson();
```

