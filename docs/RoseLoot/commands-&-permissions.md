## Introduction
This page contains all of the commands and permissions for RoseLoot.  Scroll past the table below if you want additional information on how to use these.

| Command | Description | Permission Node |
| --- | --- | --- |
| `/loot` | Shows the current plugin version and the plugin author.  The permission for the base command is given by default and can only be revoked. | roseloot.basecommand |
| `/loot help` | Displays a list of the plugin's commands. |  |
| `/loot reload` | Reloads all of the plugin's files and applies any saved changes made to them. | roseloot.reload |
| `/loot list` | Displays a tree of the loaded loot table folders/files. | roseloot.list |
| `/loot generate <lootTable> [player] [silent]` | Runs a loot table for a player and drops the loot on top of them.  If a player is not provided, will use the player who executed the command.  Silent can be set to true to avoid printing a message to the player given the loot. | roseloot.generate |
| `/loot giveitems <lootTable> [player] [silent]` | Gives all items in a loot table to a player and drops the loot on top of them.  If a player is not provided, will use the player who executed the command.  Silent can be set to true to avoid printing a message to the player given the loot. | roseloot.giveitems |
| `/loot copy [true|false]` | Creates a config entry of the player's held item to copy and paste into a loot table.  Boolean can be true to copy the NBT of the item; [NBT API](https://www.spigotmc.org/resources/7939/) plugin required. | roseloot.copy |
| `/loot copycomponents` | Creates a config entry of the player's held item using components to copy and paste into a loot table.  Only available in 1.21.3+. | roseloot.copycomponents |
| `/loot spawn <lootTable> <world> <x> <y> <z> [player]` | Runs a loot table, optionally for a player, and drops the loot at the given location. | roseloot.spawn |

## How do I use this?
### Permission Usage
To use these commands, you are required to have the permission nodes that are associated with them.  If you are /OP on your server, you are typically given all of the permissions for your plugins, so you don't have to assign them manually.

If you are not someone to give OP status to all of your members (which is definitely something that most people avoid!), you will need a permissions plugin in order to assign these permissions to your members.  We suggest using [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) to set up permissions.  It has an extensive wiki that explains everything you need to know in order to set it up.

### Command Usage
Aliases for RoseLoot commands include `/loot`, `/roseloot`, and `/rl`.  You can use any of these to replace the `/loot` that appears before the command arguments that are listed above.  The `/rl` alias may not work as it is also an alias for the built-in server `/reload` command.

For these commands, if you ever see text within `<`brackets`>`, you will need to include them in your command arguments.  Arguments are things that you need to include in the command to make them work in the way that you want.  You will ignore the brackets themselves, but will write what you want in place of the listed argument.

### Additional Help
If something is confusing to use, please [visit our Discord server](https://discord.gg/MgUsTBK) for more help.  We can't offer support for any issues or setup for permissions plugins, but we can help you with any RoseLoot issues or questions you might have.
