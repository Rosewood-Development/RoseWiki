![](RoseChatBanner.png)

## What is RoseChat?
RoseChat is a chat plugin that allows you to format chat with channels, colors, placeholders, emojis, and more!

## Support
If you need any help with our plugins, including any questions to ask, any bugs to report, or you just want to chat, [join our Discord server](https://discord.gg/MgUsTBK)!  We offer all support through our server, so feel welcome to join if you need any assistance.

## Download & Installation
### How to Install
To install the plugin, [visit our Spigot page](https://www.spigotmc.org/resources/) and hit the big download button. This will download a jar file.  Make sure your server is turned off first, and then put that jar file into your server's `/plugins` folder.  After it's in the folder, go ahead and start up your server.  After your server is finished starting up, you should be able to find a RoseChat folder in the `/plugins/RoseChat` directory, which contains all of the configuration files and data files for RoseChat.
### Dependencies
RoseChat is fully designed to work on its own, however the plugin heavily benefits from the use of other plugins.  [Vault](https://www.spigotmc.org/resources/vault.34315/) is recommended as it allows RoseChat to check the group/rank of a player.  [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) is also recommended to get more functionality out of RoseChat by using PlaceholderAPI placeholders in the chat format.  [DiscordSRV](https://www.spigotmc.org/resources/discordsrv.18494/) can be used to link RoseChat and Discord together.  [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/) is required for players to be able to delete messages.

### Alternative Download & Installation
In a more advanced method, you can compile the plugin yourself from the GitHub.
RoseChat uses Gradle to compile and build the plugin.  To use this method, run `./gradlew build` in the project's root directory to build the jar.  The plugin jar should be located in `./build/libs` when finished.