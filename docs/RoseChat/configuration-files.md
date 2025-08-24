## Introduction
RoseChat has several different configuration files that can be used to edit many different aspects of the plugin. Each config file has comments explaining the settings, but further information will be explained below.

## config.yml
The config file is used to edit most settings in the plugin. Please read the comments explaining each setting to understand what it does.
One section that is particularly useful is the `chat-formats` section:

```yaml
chat-formats:

  # The format of a /message sent to another player.
  # Default: {message-sent}{message}
  message-sent: '{message-sent}{message}'

  # The format of a /message received from another player.
  # Default: {message-received}{message}
  message-received: '{message-received}{message}'

  # The format of a spied /message.
  # Default: {spy-prefix}{spy-players}{message}
  message-spy: '{spy-prefix}{spy-players}{message}'

  # The format of a group message.
  # Default: {group-prefix}{group-member-prefix}{player}{separator}{message}
  group: '{group-prefix}{group-member-prefix}{player}{separator}{message}'
```

These are used by RoseChat to decide the format of the message that should be sent to the players. Each item surrounded by `{}` are placeholders that are defined in [custom-placeholders.yml](configuration-files.md#custom-placeholdersyml). These can be chained together to create a format perfect for you.

## channels.yml
The channels file is used to define your own custom chat channels that can be used in-game. There are a few default channels to display how they work.

### Channel Options
| Option      | Description | Example |
| -           | -           | -       |
| `default`   | This sets the channel as the default channel. <br/> Players will be placed into this channel when they first join the server. <br/> There can only be one default channel. | `default: true`
| `formats`    | The different formats used by the channel. <br/>Uses placeholders defined in the custom-placeholders.yml file. If no format is defined, the default channel's format will be used. | `formats:`<br/>`    chat: '{prefix}{player}{separator}{message}'`
| `commands`   | This creates command aliases for the channel. Players can then use that command to join the channel. | `commands:` <br> `  - staff` |
| `radius`    | The radius defines the distance that chat messages can be read from. If two players are over `radius` blocks away from each other, they will not be able to read the others' message. | `radius: 200` |
| `worlds`     | The worlds that the player has to be in to send and receive messages. | `worlds:` <br>`  - skyblock`
| `auto-join` | If this is enabled, and combined with a `world` setting, when a player enters the world they will also join the channel. | `auto-join: true`
| `visible-anywhere` | If this is enabled, players in this channel will be able to see the messages while they're using another channel. | `visible-anywhere: true`
| `joinable` | If this is enabled, the channel can be joined with a command. Disable this to stop players using a command to join. <br/> This can be combined with `visible-anywhere` and `world` to only allow players to talk in the channel with a command, or when in a specific world. <br/> This is enabled by default. | `joinable: false` |
| `discord` | The DiscordSRV channel that messages can be sent and received from. <br/> This needs to match a channel defined in DiscordSRV's config file. <br/>Requires [DiscordSRV](https://www.spigotmc.org/resources/discordsrv.18494/) installed. | `discord: global` |
| `servers` | This allows messages to be sent to the listed servers. <br/> This needs to match a server defined in bungeecord.yml. <br/> Requires BungeeCord. | `servers:`<br/>`  - skyblock` |
| `keep-format` | This allows this channel's format to be sent over bungee servers. This is very useful when you have placeholders for a specific player on one server, and need them on the second server. <br/>Requires BungeeCord. | `keep-format: true` |
| `override-commands` | This allows another plugin's commands to be overriden, so chat messages can be sent via RoseChat instead. For example, overriding the command `island chat` will allow players to use `/island chat` to talk in this channel. | `override-commands: ` <br> `  - 'island chat'`
| `shout-commands` | This allows a player to use a prefix in their message to send that message to another channel. For example, `!hello` could send `hello` to the global channel. | `shout-commands: ` <br> `  - ! ` |
| `join-conditions` | This allows you to specify conditions for a player to be able to join the channel. | `join-conditions: ` <br> `  - "%playerpoints_points%>100"` |
| `receive-conditions` | This allows you to specify conditions for a player to be able to receive messages in the channel. | `receive-conditions: ` <br> `  - "%playerpoints_points%>100"` | | 

Other options in channels.yml are related to specific plugins, these can be viewed [here](plugin-support.md).

### Formats
Each channel can have several different formats used in different places.
The default `global` channel has the following formats:
```yaml
global:
  formats:
    chat: '{prefix}{player}{separator}{message}'
    minecraft-to-discord: '{discord}'
    discord-to-minecraft: '{from-discord}{discord-player}{separator}{message}'
    shout: '&8[&3SHOUT&8]&f {prefix}{player}{separator}{message}'
    broadcast: '&8[&cBroadcast&8]&f {message}'
    join-message: "&eWelcome to the &bGlobal Channel&e!"
  # The rest of the channel settings should be placed below.
  default: true
  visible-anywhere: true
```

The `chat` format is used when a player sends a message in the channel.<br/>
The `minecraft-to-discord` format is used when a message in the channel is sent to Discord. Requires DiscordSRV.<br/>
The `discord-to-minecraft` format is used when a message is sent from Discord to the channel. Requires DiscordSRV.<br/>
The `shout` format is used with the `shout-commands` setting, and a message is shouted.<br/>
The `broadcast` format is used when a message is sent the channel from `/broadcast`.<br/>
The `join-message` format is the message sent to a player when they join the channel.<br/>

## Filters
The filters folder allows organising multiple files with filters defined inside them.<br/>
Filters can edit or block messages, such as blocking swear words, censoring them, or adding emojis and colours.<br/>
The default file `colors.yml` defines tag-based colours like `<red>` to make text red, `fun.yml` defines some fun and useful features like emojis or `@Player` tags, and `swears.yml` shows how to block or censor a word.

A filter must first start with one or more `matches`, which tells the plugin what to search for in a message. They may optionally also contain a `replacement`, which tells the plugin what to replace the matched word with.

This basic filter replaces the input of `:example:` to `\uE000`, which represents an emoji.<br/>
The `can-toggle` setting allows the /toggleemoji command to be used, this allows players to not format specific replacements, like not converting `<3` to `❤️`.<br>
These emojis can have icons when using a [Resource Pack](resource-packs.md).
```yaml
example:
  matches:
    - ":example:"
  can-toggle: true
  replacement: "\uE000"
```

There are many configuration options for filters.
```yaml
example:
  matches:
    - ":example:"
  can-toggle: true
  hover: "&b&o:rosewood:"
  replacement: "\uE000"
  escapable: true
```
The `hover` option allows a filter to be hovered over.<br>
The `escapable` option allows typing `\:example:` to prevent the filter from being used. The permission `rosechat.escape` is required.<br><br>
You can also use a custom placeholder here.
```yaml
  replacement: "{your-placeholder}"
```

There are two ways to use permissions in filters, a `use` permission and a `bypass` permission. 
The player also needs `rosechat.filters.<location>` to send replacements in a specific location.<br>
These are formatted like so:
```yaml
replaceable-words:
  matches:
    - 'crap'
  replacement: 'cr*p'
  permission:
    bypass: "rosechat.admin"
```
This `bypass` permission ensures the filter will **not** be applied for that player.

```yaml
star:
  matches:
    - ':star:'
  replacement: "✸"
  permission:
    use: rosechat.filter.star
```
This `use` permission ensures that the player must have this permission to use the filter.<br/>

```yaml
rainbow:
  matches:
    - "&h"
  replacement: "<r:0.5>"
  color-retention: true
```
The `color-retention` option allows the color specified in the output text to continue along the message.

```yaml
regex-url:
  # Regex matches can also be used.
  matches:
    - '(?:http(?:s){0,1}://){0,1}[-a-zA-Z0-9@:%._\+~#=]{2,32}\.[a-zA-Z0-9()]{2,16}\b(?:[-a-zA-Z0-9()@:%_\+.~#?&//=]*)'
  use-regex: true
  replacement: "{url}"
```
The `use-regex` option allows the `text` value to be seen as regex, and replacements will be matched against it.<br>
For filters that use regex, there are placeholders for regex groups. These can be used in linked custom placeholders, or in the `text` option itself.<br>
```yaml
spoiler-tag:
  text:
    default: "&0⬛"
  hover:
    default:
      - "%input_1%"
```
This filter uses `%input_1%` to get the text inside the spoiler tags. These can also be used in inline .<br>
The `input` placeholder allows grabbing a regex group while also checking a player's permission. Using `%group_1%` would return the first group and also parse the message without checking permissions, applying colours even if the player does not have permission to use colours in chat.

### Prefixed Filters

```yaml
spoiler:
  prefix: "<spoiler>"
  suffix: "</spoiler>"
  replacement: "{spoiler-tag}"
  match-length: true
```

Filters can also have a `prefix` and a `suffix`. This example will match this text: `<spoiler>Hello</spoiler>` and replace it with the custom placeholder `{spoiler-tag}`.<br>
The `match-length` option is useful as the `{spoiler-tag}` setting contains one character, `match-length` will repeat this character 5 times as `Hello` has 5 characters.<br>
`prefix` and `suffix` can also contain regex if `is-regex` is enabled.

```yaml
player:
  input:
    prefix: '@'
    stop: '[\p{P}\p{S}]'
  output:
    text: '{player-tag}'
    tag-online-players: true
    sound: minecraft:block.note_block.pling
```
Filters can also have only a `prefix` option. This example will look for words starting with `@` and replace them with the output text.<br>
The `stop` setting is a regex string, telling the plugin where to stop looking after it finds the prefix. This example searches for `@player` and stops when it finds punctuation or a space.<br>
The output option `tag-online-players` highlights the player's name, and sends them a sound, specified in the `sound` option.

### Inline Filters

```yaml
url:
  prefix: '['
  suffix: ']'
  inline-matches:
    - '(?:http(?:s){0,1}://){0,1}[-a-zA-Z0-9@:%._\+~#=]{2,32}\.[a-zA-Z0-9()]{2,16}\b(?:[-a-zA-Z0-9()@:%_\+.~#?&//=]*)'
  use-regex: true
  inline-prefix: '('
  inline-suffix: ')'
  replacement: "{url}"
```
This filter converts `[Click Here](www.example.com)` to `Click Here`, with the link `www.example.com`. <br>
The `prefix` and `suffix` values define the prefix and suffix for the content, `Click Here`.<br>
The `inline-prefix` and `inline-suffix` values define the prefix and suffix for the inline, `www.example.com`<br>
These can be used without regex, and without the `text` value to allow players to create their own hoverable messages. For example, `[Hover Me!](Hello)`, when configured, will create a message saying "Hover Me", and the hover says "Hello".<br>

Using a `text` value combined with `is-inline-regex`, allows the text between the `inline-prefix` and `inline-suffix` to be matched. This example matches against a URL.<br>
You can also use `is-content-regex` to match text between the `prefix` and `suffix`.<br>

The `discord-output` option, requiring DiscordSRV, allows the output to be different if sent to Discord.
```yaml
  discord-output: ":smile:"
```

### Swear Filters
You may want to stop players from sending messages with bad words in them.
The `block` option stops a message from being sent.
```yaml
bannable-words:
  matches:
    - damn
  sensitivity: 20
  block: true
  commands:
    server:
      - warn %player% Swearing
```
The default `bannable-words` filter in `swears.yml` blocks the message being sent if it finds "damn", it then also runs a command on the server to warn the player.<br>
The `sensitivity` option provides an easy way to filter similar words without having to type them all. This filter will catch `damn`, `dámn` and other variations.
A filter with a sensitivity that is too high may catch incorrect words, like `dam`, in this instance, the sensitivity can be lowered or removed entirely. 
There may be some instances where creating a second filter with a different sensitivity value may be more useful than editing the sensitivity of one.<br>
These options may also be used in other filters.

## custom-placeholders.yml
The placeholders file is used to define placeholders that RoseChat uses. This is probably the most useful file. 
It allows you to define different hover and click events based on different conditions. These can then be put together in a format to display that content to the players. The `{message}` placeholder is reserved for displaying messages, creating a placeholder called `message` will not do anything. <br>

A basic setup guide can be found [here](setup-guide.md).<br>

### Creating a Placeholder
A placeholder must first start with an ID, called `player` in this instance. This can be anything.
```yaml
player:
  text:
    default: "%player_nickname%"
  hover:
    default:
      - "&7Username: &f%player_name%"
      - "&7Click to Message"
  click:
    action: SUGGEST_COMMAND
    default: "/msg %player_name% "
```
The `text` section tells the placeholder that text must be shown. This is required.<br/>
`default` is required if no condition (explained below) is defined.<br/>
The `hover` section tells the placeholder that a hover event should be shown. This is when a player hovers over the message. As hover events can have multiple lines, this is a list. This section is optional.<br/>
The `click` section tells the placeholder that a click event should be shown. This is when a player clicks the message. Click events have [actions](https://javadoc.io/doc/net.md-5/bungeecord-chat/latest/net/md_5/bungee/api/chat/ClickEvent.Action.html) that define what they do, and values which define what the content of the action is. In this example, the `value` will be shown in the player's text box when they click the message.

### Conditional Placeholders
Placeholders can also have conditions. These bring futher customizability to them. Conditions are exactly what they sound like, a condition must be hit for a placeholder to be shown. However, in RoseChat you can also show something if a condition is not met.

```yaml
prefix:
  text:
    condition: "%vault_rank%"
    default: "&7"
    admin: "&8[#C0FFEEAdmin&8] #C0FFEE"
  hover:
    condition: "%vault_rank%"
    admin:
      - "&cThis player administrates the server!"
```
This works similarly to the previous example, but using conditions to drive what is shown. In this instance the placeholder `%vault_rank%` is the condition. If the rank is `admin`, then the admin prefix will be shown and when hovered, the admin hover event will be shown. This works the same for click events.

### Conditions
Conditions can work in a variety of ways. These are an example of how conditions are formatted in RoseChat.<br/>
Conditions can have operations in them, for example:

| Condition | Definition | Example | Meaning |
| -         | -          | -       | -       |
| `=`       | Is equal to | `%group_owner%=%player_name%` | If the group owner is the same as the player viewing the message, this will be true |
| `!=`      | Is not equal to | `%group_owner%!=%player_name%` | If the group owner is **not** the same as the player viewing the message, this will be true |
| `^`       | Contains | `%vault_rank%^staff` | If the rank includes "staff", this will be true. |

#### Strings
If a condition returns a word (not a number or true/false value), this format can be used:
```yaml
  text:
    condition: "%vault_rank%"
    default: "&7"
    vip: "&a"
    vip+: "&2"
    helper: "&9"
```
If the condition returns one of the values below it, that value will be used. If not, `default` will be used.

#### Numbers
If a condition returns a number, this format can be used:
```yaml
  text:
    condition: "%playerpoints_points%"
    value: 500
    more: "&eYou're rich!"
    equal: "&fYou've got exactly 500 points!"
    less: "&7You should earn more points..."
```
If the condition (the amount of points that the player has) is more than the value, then `more` will be used. If the condition is the same as the value, then `equal` will be used. If the condition is less than the value, then `less` will be used.
You do not need `more`, `equal` and `less` if you do not plan on using them, having a `default` value can work if you only need one.

#### Booleans (True/False)
If a condition returns true or false (or yes or no in PlaceholderAPI), this format can be used:
```yaml
  text:
    condition: "%group_owner%=%player_name%"
    default: ""
    true: "&e:star:"
    false: ""
```
If the condition is true, the `true` value will be used. If the condition is false, the `false` value can be used. If, for any reason, the placeholder cannot be parsed, then `default` will be used. It may be easier to only include `default` and `true` if both `default` and `false` are the same.

Boolean conditions can also be OR'd. This means, you can check if one condition OR another condition is true, for example:
```yaml
  text:
    condition: "%player_ping%<20||%playerpoints_points%>500"
    true: "&bCool "
```
In this condition, if the player has less than 20 ping or they have more than 500 points, then the prefix `&bCool ` is applied.

#### Multiple Conditions
If you want to use multiple conditions at once, a comma can be used like this:
```yaml
  text:
    condition: "%vault_rank%,%player_biome%"
    default,default: "&7Default "
    default,beach: "&6Sandy "
    admin,beach: "&6Sandy &cAdmin "
    
```
If the player is `default`, or has a rank not listed, then the first condition will return `default`. After this, the second condition is checked, if they are in a biome that is not listed, the second condition will also return `default`, causing the prefix to be `&7Default `.
However, if the player is in a beach, then the prefix will be `&6Sandy `. If the player is an admin, and in a beach, their prefix will be `&6Sandy &cAdmin `. 

Multiple conditions can also work with boolean conditions, for example:
```yaml
  text:
    condition: "%vault_rank%,%playerpoints_points%>500"
    admin,true: "&aA Rich Admin "
```

### Discord Embeds
When using DiscordSRV, an embed can be used to display messages. By default, just a simple message is used.
In order to use embeds, these are all the available options that can be in the placeholder:
```yaml
discord:
  title:
    default: "Title"
  description:
    default: "{message}"
  color:
    default: "#C0FFEE"
  timestamp:
    default: true
  author:
    name:
      default: "%player_displayname%"
    url:
      default: "www.example.com"
    icon-url:
      default: "www.example.com"
  image:
    url:
      default: "www.example.com"
  thumbnail:
    url:
      default: "www.example.com"
  footer:
    text:
      default: "My Footer"
    icon-url:
      default: "www.example.com"
  fields:
    # There can be as many fields as you want! Just change the id from `1` to anything!
    1:
      name: "Field"
      value: "Value"
      inline: true
    2:
      name: "Field 2"
      value: "Value 2"
      inline: true
```
These are all the options used for a discord embed. One setting, either `title` or `description` must include the `{message}` placeholder, so that the message can be shown.
Here is a basic example of an embed: <br/>
![image](https://user-images.githubusercontent.com/46502463/192036368-55ec5548-7866-4281-aef6-608eb79d724e.png)



### Default Placeholders
RoseChat has some placeholders that do not require PlaceholderAPI.

| Placeholder            | Definition                          |
| -                      | -                                   |
| `%player_name%`        | The name of the player who sent the message. |
| `%player_displayname%` | The display name of the player who sent the message. |
| `%player_nickname%`     | The nickname (from using /nick) of the player who sent the message. <br/>If a player does not have a nickname, then the display name will be used.<br/>If the player does not have a display name, then the name will be used. |
| `%group%`              | If sent in a group, the ID of the group a message is sent in. |
| `%group_name%`         | If sent in a group, the name of the group a message is sent in. |
| `%group_owner%`        | If sent in a group, the name of the owner of a group a message is sent in. |
| `%channel%`            | If sent in a channel, the name of the channel a message is sent in. |

Placeholders can also be prefixed with "other_" to get the person viewing the message, rather than the sender.
For example, `%other_player_name%` gets the name of the viewer.
