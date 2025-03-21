## Introduction
This page contains all of the commands and permissions for PlayerPoints.

| Command       | Description   | Permission Node |
| -             | -             | -               |
| `/points`       | Shows the current plugin version and the plugin author. |  |
| `/points help`  | Displays a list of the plugin's commands. |  |
| `/points reload`| Reloads all of the plugin's files and applies any saved changes made to them. | playerpoints.reload |
| `/points pay <name> <amount>` | Transfers the specified amount of points from your balance to another player. | playerpoints.pay |
| `/points give <name> <amount>` | Gives the target player a specified amount of points. | playerpoints.give |
| `/points giveall <amount>` | Gives points to all online players. | playerpoints.giveall |
| `/points take <name> <amount>` | Take points from a player. | playerpoints.take |
| `/points set <name> <amount>` | Set a player's points to the specified amount. | playerpoints.set |
| `/points reset <name>` | Resets a player's points back to 0. | playerpoints.reset |
| `/points look <name>` | View how many points a player has. | playerpoints.look |
| `/points me` | View how many points you have. | playerpoints.me |
| `/points lead [next/prev/#]` | View a page of the points leaderboard. | playerpoints.lead |
| `/points broadcast <name>` | Broadcasts a player's points. | playerpoints.broadcast |
| `/points export` | Exports the points data to storage.yml. | playerpoints.export |
| `/points import` | Imports the points data from storage.yml. | playerpoints.import |

## How do I use this?

### Permission Usage
To use these commands, you are required to have the permission nodes that are associated with them.  If you are /OP on your server, you are typically given all of the permissions for your plugins, so you don't have to assign them manually.

If you are not someone to give OP status to all of your members (which is definitely something that most people avoid!), you will need a permissions plugin in order to assign these permissions to your members.  We suggest using [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) to set up permissions.  It has an extensive wiki that explains everything you need to know in order to set it up.

### Command Usage
Aliases for RoseLoot commands include `/points`, `/playerpoints`, and `/p`.  You can use any of these to replace the `/points` that appears before the command arguments that are listed above.

For these commands, if you ever see text within `<`brackets`>`, you will need to include them in your command arguments.  Arguments are things that you need to include in the command to make them work in the way that you want.  You will ignore the brackets themselves, but will write what you want in place of the listed argument.

### Additional Help
If something is confusing to use, please [visit our Discord server](https://discord.gg/MgUsTBK) for more help.  We can't offer support for any issues or setup for permissions plugins, but we can help you with any PlayerPoints issues or questions you might have.