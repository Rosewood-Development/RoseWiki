## Introduction
RoseChat supports creating channels for many different plugins, some of which have specific options that can be configured. 
These options should be in the `channels.yml` file, when creating a channel.
Other channel options, such as world and local channels, are supported with these channels.

### BentoBox
```yaml
# The ID of the channel.
island:
  # The format for the channel.
  format: "{island-prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: BentoBox
  # This option allows you to create several channels for different ranges of players.
  # TEAM - Sends messages to members of the same island.
  # LOCAL - Sends messages to players standing on the island, even if they are not in the same team.
  # COOP - Sends messages to players who are coop/trusted.
  channel-type: TEAM
  # If this is enabled, when a player joins an island they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their island.

### FabledSkyblock
```yaml
# The ID of the channel.
island:
  # The format for the channel.
  format: "{island-prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: FabledSkyblock
  # This option allows you to create several channels for different ranges of players.
  # TEAM - Sends messages to members of the same island.
  # LOCAL - Sends messages to players standing on the island, even if they are not in the same team.
  channel-type: TEAM
  # If this is enabled, when a player joins an island they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their island.

### FactionsUUID
```yaml
# The ID of the channel.
faction:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: FactionsUUID
  # This option allows you to create several channels for different ranges of players.
  # FACTION - Sends messages to members of the same faction.
  # ALLY - Sends messages to members of ally factions.
  # MOD - Sends messages to mods of the same faction.
  # TRUCE - Sends messages to members of truced factions.
  channel-type: FACTION
  # If this is enabled, when a player joins a faction they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their faction.

### IridiumSkyblock
```yaml
# The ID of the channel.
island:
  # The format for the channel.
  format: "{island-prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: IridiumSkyblock
  # This option allows you to create several channels for different ranges of players.
  # TEAM - Sends messages to members of the same island.
  # LOCAL - Sends messages to players standing on the island, even if they are not in the same team.
  # TRUSTED - Sends messages to players who are coop/trusted.
  channel-type: TEAM
  # If this is enabled, when a player joins an island they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their island.

### KingdomsX
```yaml
# The ID of the channel.
kingdom:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: KingdomsX
  # This option allows you to create several channels for different ranges of players.
  # NATION - Sends messages to members of the same nation.
  # KINGDOM - Sends messages to members of the same kingdom.
  # ALLY - Sends messages to members of ally kingdoms.
  # TRUCE - Sends messages to members of truced kingdoms.
  # ENEMY - Sends messages to members of enemy kingdoms.
  channel-type: TEAM
  # If this is enabled, when a player joins a kingdom they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their kingdom.

### MarriageMaster
```yaml
# The ID of the channel.
mm:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: MarriageMaster
  # If this is enabled, when a player gets married, they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they divorce.

### mcMMO
```yaml
# The ID of the channel.
party:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: mcMMO
  # If this is enabled, when a player joins a party they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their party.

### SimpleClans
```yaml
# The ID of the channel.
clan:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: SimpleClans
  # This option allows you to create several channels for different ranges of players.
  # CLAN - Sends messages to members of the same clan.
  # ALLY - Sends messages to allies.
  channel-type: CLAN
  # If this is enabled, when a player joins a clan, they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their clan.

### SuperiorSkyblock
```yaml
# The ID of the channel.
island:
  # The format for the channel.
  format: "{island-prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: SuperiorSkyblock2
  # This option allows you to create several channels for different ranges of players.
  # TEAM - Sends messages to members of the same island.
  # LOCAL - Sends messages to players standing on the island, even if they are not in the same team.
  # COOP - Sends messages to players who are coop/trusted.
  channel-type: TEAM
  # If this is enabled, when a player joins an island they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their island.

### Towny
```yaml
# The ID of the channel.
town:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: Towny
  # This option allows you to create several channels for different ranges of players.
  # TOWN - Sends messages to members of the same town.
  # NATION - Sends messages to members of the same nation.
  channel-type: TOWN
  # Should allies be included in the message recipients?
  use-allies: true
  # If this is enabled, when a player joins a town they will automatically move into this channel.
  auto-join: true
```
Players will be automatically kicked from channels when they leave, or are kicked, from their town.

### WorldGuard
```yaml
# The ID of the channel.
region:
  # The format for the channel.
  format: "{prefix}{player}{separator}{message}"
  # This option specifies the plugin that this channel supports.
  plugin: WorldGuard
  # This is a list of regions that players can **not** receive messages in.
  # If a player is in region1 or region2, they will not see the messages.
  # If a player is not in region1 or region2, they **will* receive the messages.
  blacklist:
    - region1
    - region2
  # This option only allows region members to use the channel.
  use-members: false
  # If this is enabled, when a player enters a region, they will automatically move into this channel.
  auto-join: true
```

### Conditional Channels
Conditional channels can be used with any other channel.<br>
Conditional channels allow players to join, or receive messages from, a channel, if a player meets a certain condition.<br>
These can be used with placeholders to allow further plugin support.<br>
These work the similarly to [custom placeholder conditions](configuration-files.md#conditions).

```yaml
conditional:
  format: "{player}{separator}{message}"
  # This join condition makes it so only players who have over 1000 points can join the channel.
  join-conditions:
    - "%playerpoints_points%>1000"
  # This receive condition makes it so only players who have over 2000 points can receive messages in the channel.
  receive-conditions:
    - "%playerpoints_points%>2000"
```
Join conditions can be treated like 'send' conditions when the channel is visible-anywhere.<br>
This can allow for channels that player's can read, but can't send messages to.

### Other Plugins
Some plugins have features that allow them to interact with chat, such as using the chat to enter custom values.<br>
Other plugins, like InteractiveChat, may heavily alter aspects of chat.<br>

In both of these instances, the `config.yml` setting `chat-event-priority` can be edited to allow different plugins to run before or after RoseChat. This make take a few attempts to find the correct priority.<br>
The `lowest` priority happens first, so if you want a plugin to cancel chat input, you should set that plugin's chat priority to `lowest` and RoseChat to a higher value.<br>

The `packet-event-priority` setting works similarly, but is most effectve when another plugin directly edits a chat message, as the delete message button may not be added correctly.

