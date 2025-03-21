## Introduction
This page contains all of the commands and permissions for RoseStacker.  Scroll past the table below if you want additional information on how to use these.

| Command       | Description   | Permission Node |
| -             | -             | -               |
| `/rs`       | Shows the current plugin version and the plugin author. The permission for the base command is given by default and can only be revoked. | rosestacker.basecommand |
| `/rs help`  | Displays a list of the plugin's commands. |  |
| `/rs reload`| Reloads all of the plugin's files and applies any saved changes made to them. | rosestacker.reload |
| `/rs give <block|spawner|entity> <player> <type> <stackSize> [amount]` | Gives the target player a bundled stack of a specified type. | rosestacker.give |
| `/rs clearall <entity|item|all>` | Clears all of the stack type from the world. | rosestacker.clearall |
| `/rs stats` | Displays stats about the plugin. | rosestacker.stats |
| `/rs translate <language> <spawnerNameOrder>` | Changes the set names for stacks in all of the settings files.  Spawner stacks cannot be properly translated due to word orders of languages, so follow the in-game prompt to re-run the command and correctly format the spawner stack names. | rosestacker.translate |
| `/rs stacktool [player]` | Gives yourself or another player the stacking tool. | rosestacker.stacktool.give |
|               | Allows a player to use the stacking tool. | rosestacker.stacktool |
|               | Allows players to pick up spawners of a certain mob with silk touch tools.  This permission is toggleable in the config.yml file.  Enable the silk-touch-advanced-permissions setting in the config.yml to use this permission.| rosestacker.silktouch.<entityType\> |
|               | Allows players to pick up spawners of a certain mob without needing silk touch tools.  Enable the silk-touch-advanced-permissions setting in the config.yml to use this permission.| rosestacker.nosilk.<entityType\> |
|               | Allows players to place spawners of a certain mob.  Enable the silk-touch-advanced-permissions setting in the config.yml to use this permission.| rosestacker.spawnerplace.<entityType\> |
|               | Allows players to use spawn eggs on stacked spawners to convert them to a different type. | rosestacker.spawnerconvert |
|               | Allows setting a configurable spawner drop chance with silk touch. Replace # with a number between 0 and 100. | rosestacker.silktouch.chance.<#> |
|               | Allows a player to kill an entire stack of mobs in one hit regardless of other settings. Requires the config setting `kill-entire-stack-on-death-permission` to be enabled to work. | rosestacker.killentirestack |

## How do I use this?

### Permission Usage
To use these commands, you are required to have the permission nodes that are associated with them.  If you are /OP on your server, you are typically given all of the permissions for your plugins, so you don't have to assign them manually.

If you are not someone to give OP status to all of your members (which is definitely something that most people avoid!), you will need a permissions plugin in order to assign these permissions to your members.  We suggest using [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) to set up permissions.  It has an extensive wiki that explains everything you need to know in order to set it up.

### Command Usage
Aliases for RoseStacker commands include `/rosestacker`, `/stacker`, and `/rs`.  You can use any of these to replace the `/rs` that appears before the command arguments that are listed above.

For these commands, if you ever see text within `<`brackets`>`, you will need to include them in your command arguments.  Arguments are things that you need to include in the command to make them work in the way that you want.  You will ignore the brackets themselves, but will write what you want in place of the listed argument.

The `/rs give` command is the most complicated command we have, so we'll give you an example of how it'd be typed: `/rs give Spawner YourUsername Sheep 5 1`

That command with those arguments will put 1 stack of 5 pre-stacked sheep spawners into the specified player's (YourUsername) inventory.

### Additional Help
If something is confusing to use, please [visit our Discord server](https://discord.gg/MgUsTBK) for more help.  We can't offer support for any issues or setup for permissions plugins, but we can help you with any RoseStacker issues or questions you might have.