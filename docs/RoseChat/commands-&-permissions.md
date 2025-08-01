## Introduction
This page contains all of the commands and permissions for RoseChat.  Scroll past the table below if you want additional information on how to use these.

| Command           | Description   | Permission Node |
| -                 | -             | -               |
| `/rc`           | Shows the current plugin version and the plugin author. The permission for the base command is given by default and can only be revoked. | rosechat.basecommand |
| `/rc help`      | Displays a list of the plugin's commands. |  |
| `/rc reload`   | Reloads all of the plugin's files and applies any saved changes made to them. | rosechat.reload |
| `/msg`         | Sends a message to another player.<br>This permission is given by default. | rosechat.message |
| `/r`            | Replies to a message sent from another player.<br>This permission is given by default. | rosechat.reply |
| `/socialspy`    | Allows a player to see private messages. | rosechat.spy
|                   | Allows a player to spy on messages sent with /msg. | rosechat.spy.message |
|                   | Allows a player to spy on messages sent in a channel. | rosechat.spy.channel |
|                   | Allows a player to spy on messages sent in a group. | rosechat.spy.group |
| `/togglemsg`    | Toggles the ability to receive messages. | rosechat.togglemessage |
|                   | Allows messaging players who have disabled receiving messages. | rosechat.togglemessage.bypass |
| `/togglesound`  | Toggles the ability to receive sounds when receiving a message or being tagged. | rosechat.togglesound |
| `/toggleemoji`  | Toggles the ability to automatically format emojis. | rosechat.toggleemoji |
| `/channel`      | Joins or sends a message in a chat channel.         | rosechat.channel |
|                   | Allows using a specific chat channel. The permission `rosechat.channel.global` is given to all players by default. | rosechat.channel.<channel\> |
|                   |  Allows joining an un-joinable channel. | rosechat.channelbypass |
| `/<channel>`  | An alias for /channel <channel>. This command is defined in `channels.yml` | rosechat.channel.<channel\> |
| `/chat`         | Displays a list of admin commands for chat channels. | rosechat.chat |
| `/chat mute`    | Mutes a chat channel. | rosechat.chat.mute |
| `/chat clear`   | Clears a chat channel. | rosechat.chat.clear |
| `/chat move`    | Moves a player to another chat channel. | rosechat.chat.move |
| `/chat sudo`    | Sends a message as another player, in a chat channel. | rosechat.chat.sudo |
| `/chat info`    | Displays info about a chat channel. | rosechat.chat.info |
| `/chat toggle`  | Disables seeing a channel. | rosechat.chat.toggle.<channel\> |
| `/chat slowmode`| Enables slow mode for a channel. | rosechat.chat.slowmode |
| `/chatcolor`    | Change your default chat color. | rosechat.chatcolor<br/>rosechat.chatcolor.others |
| `/mute`         | Mutes a player. | rosechat.mute |
| `/unmute`       | Removes a player's mute. | rosechat.unmute |
|                   | Stops the player from being able to be muted. | rosechat.mute.bypass |
| `/group`        | Displays a list of group chat commands. | rosechat.group |
| `/group create` | Creates a new group chat. | rosechat.group.create |
| `/group disband`| Deletes a group chat. | rosechat.group.disband |
| `/group invite` | Invites a player to your group chat. | rosechat.group.invite |
| `/group kick`   | Kicks a player from your group chat. | rosechat.group.kick |
| `/group accept` | Accepts a group invite. | rosechat.group.accept |
| `/group deny`   | Denies a group invite. | rosechat.group.deny |
| `/group leave`  | Leaves a group chat. | rosechat.group.leave |
| `/group members`| Displays the members in the group chat. | rosechat.group.members |
| `/group info`   | Displays info about a group chat. | rosechat.group.info |
| `/group promote`| Promote a group member to owner. | rosechat.group.promote |
|                   | Allows managing groups that you do not own. <br/>For example, using `/group disband <group>` to delete a group that you do not own. | rosechat.group.admin |
|                   | Limits the amount of group chats a player can be in. | rosechat.groups.<#> | 
| `/gmsg`         | Sends a message in a group chat. | rosechat.group.message |
| `/nickname`     | Change your own, or another players, nickname. | rosechat.nickname<br/>rosechat.nickname.others |
|                   | Allows bypassing configured nickname settings. | rosechat.nickname.bypass.min <br/> rosechat.nickname.bypass.max <br/> rosechat.nickname.bypass.space <br/> rosechat.nickname.bypass.nonalpha |
| `/nickcolor`    | Change the color of your nickname.<br/>This uses the same permissions as nicknames. For example, rosechat.color.nickname| rosechat.nickcolor<br/>rosechat.nickcolor.others |
|                   | Allows a player to edit their nickname. <br/>This is given to everyone by default.<br/>When negated, a player will only be able to add colors to their nickname.<br/>For example, `Lilac` could change to `&cLilac`, but not `Lilaaac`.| rosechat.nickname.edit |
| `/ignore`       | Ignores messages from another player. <br/>/ignorelist can be used to list the players that are ignored.| rosechat.ignore |
|                   | Stops other players from being able to ignore this player. | rosechat.ignore.bypass |
| `/realname`     | Allows a viewing the realname of a player.               | rosechat.realname      |
| `/broadcast`    | Broadcasts a message to the server or specific channel. Placeholders can be freely used in broadcasts. | rosechat.broadcast |
| `/emoji`        | Allows users to view and test their emojis by sending a message to themselves. | rosechat.emoji |
| `/ping`         | Replies back to a player with what they sent, including emojis, replacements, and placeholders. | rosechat.ping |
|                   | Required for players to click the delete message button. | rosechat.deletemessage |
|                   | Allows players to delete messages sent from the server to the player. <br/> For example, `<player> has joined the server`. | rosechat.deletemessages.client |
|                   | Allows players to delete their own messages. | rosechat.deletemessages.self |
|                   | Allows players to delete other player's messages. | rosechat.deletemessages.others |
|                   | Allows players to see deleted messages. <br/> It is required to have a format that displays the deleted message for this to work. | rosechat.deletemessages.see |
|                   | Allows using color codes in different places. | rosechat.color.channel.<channel\> <br/> rosechat.color.chatcolor <br/> rosechat.color.group <br/> rosechat.color.message <br/> rosechat.color.nickname |
|                   | Allows using shadow color codes in different places. | rosechat.shadow.color.channel.<channel\> <br/> rosechat.shadow.color.chatcolor <br/> rosechat.shadow.color.group <br/> rosechat.shadow.color.message <br/> rosechat.shadow.color.nickname |
|                   | Allows using bold (&l or \*\*) in different places. | rosechat.bold.channel.<channel\> <br/> rosechat.bold.chatcolor <br/> rosechat.bold.group <br/> rosechat.bold.message <br/> rosechat.bold.nickname |
|                   | Allows using underline (&n or __) in different places. | rosechat.underline.channel.<channel\> <br/> rosechat.underline.chatcolor <br/> rosechat.underline.group <br/> rosechat.underline.message <br/> rosechat.underline.nickname |
|                   | Allows using strikethrough (&m or ~~) in different places. | rosechat.strikethrough.channel.<channel\> <br/> rosechat.strikethrough.chatcolor <br/> rosechat.strikethrough.group <br/> rosechat.strikethrough.message <br/> rosechat.strikethrough.nickname |
|                   | Allows using italic (&o or \*) in different places. | rosechat.italic.channel.<channel\> <br/> rosechat.italic.chatcolor <br/> rosechat.italic.group <br/> rosechat.italic.message <br/> rosechat.italic.nickname |
|                   | Allows using magic (&k) in different places. | rosechat.magic.channel.<channel\> <br/> rosechat.magic.chatcolor <br/> rosechat.magic.group <br/> rosechat.magic.message <br/> rosechat.magic.nickname |
|                   | Allows using hex colors in different places. | rosechat.hex.channel.<channel\> <br/> rosechat.hex.chatcolor <br/> rosechat.hex.group <br/> rosechat.hex.message <br/> rosechat.hex.nickname |
|                   | Allows using shadow hex colors in different places. | rosechat.shadow.hex.channel.<channel\> <br/> rosechat.shadow.hex.chatcolor <br/> rosechat.shadow.hex.group <br/> rosechat.shadow.hex.message <br/> rosechat.shadow.hex.nickname |
|                   | Allows using gradient formatting in different locations. | rosechat.gradient.channel.<channel\> <br/> rosechat.gradient.chatcolor <br/> rosechat.gradient.group <br/> rosechat.gradient.message <br/> rosechat.gradient.nickname |
|                   | Allows using shadow gradient formatting in different locations. | rosechat.shadow.gradient.channel.<channel\> <br/> rosechat.shadow.gradient.chatcolor <br/> rosechat.shadow.gradient.group <br/> rosechat.shadow.gradient.message <br/> rosechat.shadow.gradient.nickname |
|                   | Allows using rainbow formatting in different places. | rosechat.rainbow.channel.<channel\> <br/> rosechat.rainbow.chatcolor <br/> rosechat.rainbow.group <br/> rosechat.rainbow.message <br/> rosechat.rainbow.nickname |
|                   | Allows using shadow rainbow formatting in different places. | rosechat.shadow.rainbow.channel.<channel\> <br/> rosechat.shadow.rainbow.chatcolor <br/> rosechat.shadow.rainbow.group <br/> rosechat.shadow.rainbow.message <br/> rosechat.shadow.rainbow.nickname |
|                   | Allows bypassing the spam filter in different locations. | rosechat.spam.channel.<channel\> <br/> rosechat.spam.group <br/> rosechat.spam.message |
|                   | Allows bypassing the language filter in different locations. | rosechat.language.channel.<channel\> <br/> rosechat.language.group <br/> rosechat.language.message <br/> rosechat.language.nickname |
|                   | Allows bypassing the caps filter in different locations. | rosechat.caps.channel.<channel\> <br/> rosechat.caps.group <br/> rosechat.caps.message <br/> rosechat.caps.nickname |
|                   | Allows bypassing the URL filter in different locations. | rosechat.links.channel.<channel\> <br/> rosechat.links.group <br/> rosechat.links.message <br/> rosechat.links.nickname |
|                   | Allows using the \`code\` markdown in different locations. | rosechat.code.channel.<channel\> <br/> rosechat.code.group <br/> rosechat.code.message <br/> rosechat.code.nickname |
| | Allows using the \```multicode\``` markdown in different locations. | rosechat.multicode.channel.<channel\> <br/> rosechat.multicode.group <br/> rosechat.multicode.message <br/> rosechat.multicode.nickname |
|                   | Allows using the `> quote` markdown in different locations. | rosechat.quote.channel.<channel\> <br/> rosechat.quote.group <br/> rosechat.quote.message <br/> rosechat.quote.nickname |
|                   | Allows using placeholders in different locations. <br/> A specific placeholder permission is also required. | rosechat.placeholders.channel.<channel\> <br/> rosechat.placeholders.group <br/> rosechat.placeholders.message <br/> rosechat.placeholders.nickname |
|                   | Allows using a specific placeholder. <br/> Example Permissions for PlaceholderAPI: `rosechat.placeholders.player.name` for `%player_name%` or `rosechat.placeholders.server.maxplayers` for `%server_max_players%`. <br/> Example Permission for RoseChat Placeholders: `rosechat.placeholders.rosechat.player` for `{player}`. | rosechat.placeholder.<placeholder\> |
|                   | Allows using replacements in different locations. <br/> A specific replacement permission is also required. | rosechat.replacements.channel.<channel\> <br/> rosechat.replacements.group <br/> rosechat.replacements.message <br/> rosechat.replacements.nickname |
|                   | Allows using a specific replacement. <br/> Example Permission: `rosechat.replacement.regex-example`. | rosechat.replacement.<replacement\> |
|                   | Allows using emojis in different locations. <br/> A specific emoji permission is also required. | rosechat.emojis.channel.<channel\> <br/> rosechat.emojis.group <br/> rosechat.emojis.message <br/> rosechat.emojis.nickname |
|                   | Allows using a specific emoji. <br/> Example Permission: `rosechat.emoji.rosewood`. | rosechat.emoji.<emoji\> |
|                   | Allows using a specific color in chat. <br/>Requires `use-per-color-permissions` in `config.yml` to be enabled. <br/>A full list of colors can be found here: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/ChatColor.html<br/> Example Permissions:<br> `rosechat.red.channel.global` - Allows using red in the global channel.<br>`rosechat.red.chatcolor` - Allows using /chatcolor &c<br>`rosechat.color.channel.global` - Allows using colours in the global channel.<br>`rosechat.color.chatcolor` - Allows using colours in /chatcolor. | rosechat.<color\>.<location\> |
|                   | Allows using the [item] replacement.                     | rosechat.helditem.channel.<channel\>      |
| | Allows seeing messages sent by players that were blocked by the plugin.<br>For example, messages containing blocked words. | rosechat.seeblocked |

## How do I use this?

### Permission Usage
To use these commands, you are required to have the permission nodes that are associated with them.  If you are /OP on your server, you are typically given all of the permissions for your plugins, so you don't have to assign them manually.

If you are not someone to give OP status to all of your members (which is definitely something that most people avoid!), you will need a permissions plugin in order to assign these permissions to your members.  We suggest using [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) to set up permissions.  It has an extensive wiki that explains everything you need to know in order to set it up.

### Command Usage
Aliases for RoseChat commands include `/rosechat` and `/rc`. You can use either of these to replace the `/rc` that appears before the command arguments that are listed above.
The /channel command has the alias `/c` which can be used instead of `/channel`.
The /group command has the alias `/gc` which can be used instead of `/group`.

For these commands, if you ever see text within `<`brackets`>`, you will need to include them in your command arguments.  Arguments are things that you need to include in the command to make them work in the way that you want.  You will ignore the brackets themselves, but will write what you want in place of the listed argument.

### Additional Help
If something is confusing to use, please [visit our Discord server](https://discord.gg/MgUsTBK) for more help.  We can't offer support for any issues or setup for permissions plugins, but we can help you with any RoseChat issues or questions you might have.