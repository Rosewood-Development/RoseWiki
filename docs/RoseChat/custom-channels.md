### Introduction
Custom channels allow you to create a channel for players to send messages in. These can be added to your own plugins to support RoseChat.

#### Examples
Examples can be found in the source code, as RoseChat creates custom channels for several different plugins.<br>
These can be found [here](https://github.com/Rosewood-Development/RoseChat/tree/master/src/main/java/dev/rosewood/rosechat/hook/channel).

One of the simplest examples would be the SimpleClans support, [here](https://github.com/Rosewood-Development/RoseChat/tree/master/src/main/java/dev/rosewood/rosechat/hook/channel/simpleclans).

#### Channel Providers
A [ChannelProvider](https://github.com/Rosewood-Development/RoseChat/blob/master/src/main/java/dev/rosewood/rosechat/hook/channel/ChannelProvider.java) provides RoseChat with information about the channels that may be needed before the channels are created.<br>

Overriding the `getChannels()` function allows channel providers to create single instances of channels. There will only ever be one of each channel.
```java
List<Class<? extends Channel>> getChannels()
```
However, overriding the `getChannelGenerator()` function allows channels to be created from a configuration section, specified when overriding `getConfigurationSection()`
```java
Class<? extends Channel> getChannelGenerator()
```

The `getSupportedPlugin()` function is necessary for RoseChat to identify the channel. Typically this would match with the supported plugin name, and this is what users will specify in the `channels.yml` file.

#### Channels
The first step to creating a channel is by extending the `RoseChatChannel` class, other classes may be used, such as `ConditionalChannel` or just `Channel`, but `RoseChatChannel` is the most useful and convenient.<br>

These classes have javadoc comments that explain what the functions do. There are several functions that you may take use of, but overriding the `getVisibleAnywhereRecipients(RosePlayer sender, World world)` function allows you to return a list of players who should receive the message when `visible-anywhere` is enabled.<br>
The `getMemberRecipients(RosePlayer sender, World world)` function allows you to return a list of players who should receive the message when `visible-anywhere` is disabled, and players can become members of the channel.<br>

There are various `send` methods in `RoseChatChannel`, but these typically do not need to be touched, as they should work as intended.

#### Registering Channels
Once your channel is created, it should be specified in either the `getChannels()` or `getChannelGenerator()` functions in the provider.<br>
After this, the channel needs to be registed using the `register()` function in the provider, like so:
```java
new YourChannelProvider().register();
```