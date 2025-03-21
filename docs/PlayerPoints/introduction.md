![](PlayerPointsBanner.png)

## What is PlayerPoints?
PlayerPoints is a simple and efficient currency plugin, adding the ability to manage points for players. Its features can be used by plugins that directly support PlayerPoints, or optionally through Vault.

## Support
If you need any help with our plugins, including any questions to ask, any bugs to report, or you just want to chat, [join our Discord server](https://discord.gg/MgUsTBK)!  We offer all support through our server, so feel welcome to join if you need any assistance.

## Download & Installation
### How to Install
To install the plugin, [visit our Spigot page](https://www.spigotmc.org/resources/playerpoints.80745/) and hit the big download button.  This will download a jar file.  Make sure your server is turned off first, and then put that jar file into your server's `/plugins` folder.  After it's in the folder, go ahead and start up your server.  After your server is finished starting up, you should be able to find a PlayerPoints folder in the `/plugins/PlayerPoints` directory, which contains all of the configuration files and data files for PlayerPoints.
### Dependencies
None!
Optionally, we support Vault and PlaceholderAPI. The hook for Vault is disabled by default but can be enabled in the config.yml.

### Alternative Download & Installation
In a more advanced method, you can compile the plugin yourself from the GitHub.
PlayerPoints uses Gradle to compile and build the plugin.  To use this method, run `./gradlew build` in the project's root directory to build the jar.  The plugin jar should be located in `./build/libs` when finished.