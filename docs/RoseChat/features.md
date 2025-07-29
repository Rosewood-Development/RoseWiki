## Introduction

## Our List of Features

### Chat Features

* Full RGB text support with permission checking
    * Legacy Minecraft Colors - Format: Use & before the a-f or 0-9<br/>
![Legacy Minecraft Colors](https://user-images.githubusercontent.com/46502463/158829737-3828bd62-c24b-48a6-ae35-f84305670ac2.png)
    * Legacy Minecraft Formatting - Format: Use & before k-o or r<br/>
![Legacy Minecraft Formatting](https://user-images.githubusercontent.com/46502463/158830754-ad74a615-419b-4663-b1e6-0e11a9e9f0f7.gif)<br>
    Formatting can also be removed by using a capital letter. For example, in `&l&oHello &Lplayer` the word `Hello` will be bold and italic, but the word `player` will no longer be bold, and only be italic.
    * 1.16+ Hex Colors - Format: #FFFFFF, &#FFFFFF, <#FFFFFF>, {#FFFFFF}<br/>
![Hex Colors](https://user-images.githubusercontent.com/46502463/158832635-8b7b66d5-b3dd-44e8-8a60-fcc9b19d8864.png)
    * Rainbow Color Formatting - Format: `<r>Text` or `<r:0.5>Text` for saturation<br/>
![Rainbow Color Formatting](https://user-images.githubusercontent.com/46502463/158832791-f15ce52a-63c3-4a23-8b53-9fe2085a4cff.png)
    * Gradient Color Formatting - Format: `<g:#000000:#FFFFFF>Text`<br/>
![Gradient Color Formatting](https://user-images.githubusercontent.com/46502463/158832897-2cb12970-c1a3-4732-a12e-4f722d53c044.png)
* Placeholders in chat with permission checking
    * Supports PlaceholderAPI<br/>
![PlaceholderAPI Placeholders](https://user-images.githubusercontent.com/46502463/158833118-20fbd662-dd90-47db-9147-33099c374473.png)
    * Supports RoseChat Placeholders<br/>
![RoseChat Placeholders](https://user-images.githubusercontent.com/46502463/158834078-c2fc3d40-b42e-4fdf-ba47-8457feb6ef4d.png)
* Chat Replacements and Filters
    * Replace words in chat
    * Supports Regex Replacements and RoseChat Formatting<br/>
![Chat Replacements](https://user-images.githubusercontent.com/46502463/158837535-2829e7f1-7a13-4a4c-8197-45f4a67c7e50.png)
* Tags
    * Tag players and play a sound when tagged
    * Add extra content to messages<br/>
![Player Tag](https://user-images.githubusercontent.com/46502463/158838219-721df534-b124-4707-adc9-c7333d3cdf69.png)
* Display Items
    * Display your held item in chat<br/>
![image](https://github.com/Rosewood-Development/RoseChat/assets/46502463/b42f8df1-c15e-4a05-9a8c-107a2a06d7fa)
* Moderation Tools
    * Spam filter with configurable sensitivity and messages<br/>
![Spam Filter](https://user-images.githubusercontent.com/46502463/158839526-0c12cc2c-acad-4bac-8b86-a338800de7fd.png)
    * Language filter with configurable words, sensitivity, and messages<br/>
![Language Filter](https://user-images.githubusercontent.com/46502463/158839769-67c49b00-2573-40d7-a284-6139bf454dbe.png)
    * Capital letters filter with configurable settings and messages<br/>
![Caps Filter](https://user-images.githubusercontent.com/46502463/158839922-3d21035d-1f93-48c8-8d87-dfeaa2ec5547.png)
    * URL/IP filtering with configurable settings and messages<br/>
![URL Filter](https://user-images.githubusercontent.com/46502463/158840602-3db11cb2-da80-491c-881a-c0cfd105330c.png)
* Discord Markdown Support
    * Use Discord formatting like such as \*\***bold**\*\* and \*_italic_\* in-game<br/>
![Discord Formatting](https://user-images.githubusercontent.com/46502463/158841206-26f5afcf-3a15-4e73-b2e6-bc989e0c14d2.png)
* Custom Emoji Support
    * Support for using a [resource pack](resource-packs.md) to add custom images, then display them in-chat or in RoseChat placeholders<br/>
![Custom Emoji](https://user-images.githubusercontent.com/46502463/158841545-af65f802-bb05-4181-b48a-e782f606f784.png)
* Core Shader Support
    * Support for using a resource pack to add core shaders, then display them in chat or in RoseChat placeholders<br/>
![Core Shaders](https://user-images.githubusercontent.com/46502463/158843105-0f6a9b4c-c38f-4cc6-abf3-c0c814d40a67.gif)
* All this is also available in nicknames, channels, group chats, and private messages with permissions for everything!

### Chat Channels

* [Many Configuration Options](configuration-files.md#channelsyml)
* Send messages in Discord channels with [DiscordSRV](https://www.spigotmc.org/resources/discordsrv.18494/)
* Send messages across BungeeCord servers
* Create staff-only or donator-only channels by giving players a permission
* Create [custom formats](configuration-files.md#custom-placeholdersyml) with placeholder support, hover events, chat events, and more
* Includes admin commands to manage channels, such as muting, clearing, moving players, or sudo-ing them
* Create a command alias, like /staff, to make chatting easier
* Supports [many plugins](plugin-support.md)!
* Create override commands, to re-route other plugin chats to RoseChat
* Create shout commands, to quickly send a message in other channels

### Group Chats

* Players can create group chats, like party chats, with their friends
* Players can invite people, or kick them from the group chat
* With a permission, admins can read messages
* With a permission, admins can manage group chats too

### Deleting Messages

* **Requires ProtocolLib**
* Players can delete messages in chat
    * Delete server messages
    * Delete your own messages
    * Delete messages sent by other players
    * See deleted messages<br/>

![Delete Messages](https://user-images.githubusercontent.com/46502463/158849317-d841d93e-0993-408f-993a-681dee5d9bd8.png)

### DiscordSRV Support

* **Requires DiscordSRV**
* Fully format Discord messages like any other RoseChat message
* Use RoseChat nicknames instead of Discord names
* Fully convert Discord messages to Minecraft messages - including emojis, channel links, and tags
* Fully convert Minecraft messages to Discord messages - including emojis, channel links, and tags
* Send message embeds to Discord to add extra content to messages
* Delete Discord messages from within Minecraft **Requires ProtocolLib**
* Edit Discord message and have them update in Minecraft **Requires ProtocolLib**