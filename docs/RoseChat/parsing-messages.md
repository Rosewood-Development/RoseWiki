The most important file of RoseChat's API is the RoseChatAPI class, which can be found [here](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/api/RoseChatAPI.java).<br>
This class contains many functions which you may find useful.<br>

The most convenient way of parsing a message is to use the `RoseChatAPI#parse()` function. This function will take a given string and parse it using RoseChat's message wrapper and message tokenizer system. This will allow colors (including hex, rainbow and gradient), emojis, tags, and everything else included in RoseChat, to be parsed.<br>

There are a few variations of this function:<br><br>

This method simply parses the message.
```java
BaseComponent[] parse(RosePlayer sender, RosePlayer viewer, String message)
```

This method allows you to use placeholders in the message.
```java
BaseComponent[] parse(RosePlayer sender, RosePlayer viewer, String message, StringPlaceholders placeholders)
```

This method allows using a [MessageLocation](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/message/MessageLocation.java) to check for permissions.
```java
BaseComponent[] parse(RosePlayer sender, RosePlayerviewer, String message, MessageLocation location)
```

#### RosePlayer
The [RosePlayer](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/message/RosePlayer.java) object is used by RoseChat to give more information to a Player object. When you need to use a RosePlayer, you can just create a `new RosePlayer()`. This object has a few different constructors, but passing a Player object through is the most common.

This is an example of how to use these together, for parsing a message when the player joins.
```java
@EventHandler
public void onPlayerJoin(PlayerJoinEvent event) {
    RoseChatAPI rosechat = RoseChatAPI.getInstance();
    Player player = event.getPlayer();
    RosePlayer rosePlayer = new RosePlayer(player);

    BaseComponent[] message = rosechat.parse(rosePlayer, rosePlayer, "<r:0.5>Hi %player_name% &r:rosewood:");
    Bukkit.spigot().broadcast(message);
}
```

When parsing a single message, this may be preferred. However, to allow multiple messages to be sent at the same time to multiple players, these should be sent asynchronously.<br>
The [RoseChatChannel](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/hook/channel/rosechat/RoseChatChannel.java) class displays how, by using the `RoseChat.MESSAGE_THREAD_POOL`.

The `parse` method creates a single `RoseMessage` object, intended to be viewed the same by any player.<br>
Creating a new `RoseMessage` object for each player allows each player to receive a message unique to them.

#### Rose Messages
The preferred way to send a message to multiple players is by using `RoseMessage.forChannel(RosePlayer, Channel)` or `RoseMessage.forLocation(RosePlayer, MessageLocation).<br>

An example of this is used in the RoseChatChannel class:
```java

        RoseMessage roseMessage = RoseMessage.forChannel(sender, this);

        // Create the rules for this message.
        MessageRules rules = new MessageRules().applyAllFilters();
        MessageRules.RuleOutputs outputs = rules.apply(roseMessage, message);

        // Check if the message is allowed to be sent.
        if (outputs.isBlocked()) {
            if (outputs.getWarning() != null)
                outputs.getWarning().send(sender);
            return;
        }

        roseMessage.setPlayerInput(outputs.getFilteredMessage());

        MessageTokenizerResults<BaseComponent[]> components = roseMessage.parse(receiver, format);
        MessageOutputs messageOutputs = components.outputs();

```

This creates a new `MessageRules` object, which defines the rules of the message, and if a message should be filtered based on the permissions of the sender. It also applies the sender's chat colour.<br>
A `RoseMessage` object is then created, passing in the sender and channel. Then the rules are applied to the sent message. At this stage, the message is changed to be filtered.<br>

Before a message is parsed, checking if `isBlocked()` may be useful to see if the filter system caught anything that should not be sent. The function `getWarning()` can provide you with the reason why the message was filtered.<br>

After this, the message is parsed with a viewer and format. This is first parsed for the console, so that the console receives the message, but also so that the `tokens` are generated and cached, allowing for further optimization.<br>
RoseChat will, essentially, cache part of the message so it does not needed to be parsed every time for every player, only when the content should change, such as a per-player placeholder.<br>
A format is not needed, and `null` can be passed.<br>

There are several `parse` functions in the `RoseMessage` class.<br>
The first simply parses the message as it should be seen in-game.
```java
BaseComponent[] parse(RosePlayer viewer, String format)
```

The second treats the message as if it was sent from Discord, converting Discord formatting to Minecraft. A discord id can be passed to allow messages to be deleted in Discord.
```java
BaseComponent[] parseMessageFromDiscord(RosePlayer viewer, String format, String discordId)
```

The third treats the message as if it was sent to Discord, converting Minecraft formatting to Discord.
```java
BaseComponent[] parseMessageToDiscord(RosePlayer viewer, String format)
```

The fourth treats the message as if it was going to be sent to a Bungee server.
```java
BaseComponent[] parseBungeeMessage(RosePlayer viewer, String format)
```

The final method allows a MessageParser to be specified, and a discord id too, if needed..
```java
BaseComponent[] parse(MessageParser parser, RosePlayer viewer, String format, String discordId)
```

Now that the message is parsed, functions such as `getTaggedPlayers()` becomes available to use from the MessageOuputs class.

### Message Parsers
A message parser is a way of deciding what to do with a message when it is parsed.<br>
Typically, this consists of combining multiple [tokenizers]() to create a final message.<br>
An example of a MessageParser can be seen [here](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/message/parser/RoseChatParser.java).<br>
This MessageParser mainly decides what tokenizers to use for the message.<br>
A MessageParser is simply called when the message is parsed, so anything can be done to the message.
