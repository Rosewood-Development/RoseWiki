## Introduction
Items determine what things will drop from the loot tables, though it is not limited to only item drops.  Each type of item has its own special kind of syntax and parameters and will be listed below.  You can use the table of contents to find specific types.

## Items
This is probably the most common type of item that you will be wanting to drop: actual items!  Making basic items is very simple, but you can do way more than that.  Below is the most simple example of how to drop an item.
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount: 1
```
Items have so many settings that they are going to be put onto a separate page, which can be found [here](item-meta.md).

## Custom Items
Support for dropping items from custom item plugins can be found [here](custom-item-plugins.md).

## Item Tags
It is possible to drop a random item from a specific tag group.  A list of possible tags can be found [here](https://minecraft.wiki/w/Tag#List_of_tags).
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:creeper'
  - 'death-cause:lightning'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: tag
            tag: creeper_music_disc_drops
            amount: 1
```
Tags support the same parameters as [Items](item-types.md).

## Entity Equipment
If an entity is capable of holding equipment or has an inventory, you can use this to drop those items.  All armor chance parameters are optional and will default to their normal drop chances if not provided.  `drop-inventory` will default to false if not provided.
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:skeleton'
  - 'required-tool:sword,stone'
  - 'enchantment:fire_aspect,2'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: entity_equipment
            helmet-drop-chance: 0.15
            chestplate-drop-chance: 0.07
            leggings-drop-chance: 0.1
            boots-drop-chance: 0.12
            main-hand-drop-chance: 0.16
            off-hand-drop-chance: 0.11
            drop-inventory: false
```

## Experience
Just as it says in the name, this will allow you to drop experience.  You can optionally drop bonus experience based on how much equipment the mob that was killed has.  To do this, create an `equipment-bonus` section with a numerical value of how much experience to add per piece of equipment.
```yaml
type: ENTITY
overwrite-existing: experience
conditions:
  - 'entity-type:skeleton'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: experience
            amount: 5
            equipment-bonus:
              min: 1
              max: 3
```

## Commands
You can run commands for those more exotic actions you want to perform from loot tables.  An optional property called `run-as-player` exists which can be set to true to run the command as the player instead of the console.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:villager'
  - 'dimension:normal'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: command
            value: 'say %player% killed a villager at %x% %y% %z% in %world%!'
            run-as-player: false
```
You can find valid placeholders to be used within commands on the [Context Placeholders](context-placeholders.md) page.

## Loot Tables
Yes, it is possible to run a loot table within another loot table.  If you're interested, the vanilla loot table for fishing uses nested loot tables like this.  You can find the vanilla loot table in RoseLoot's format in the default examples.
```yaml
type: ENTITY
conditions:
  - 'entity-type:glow_squid'
  - 'glow-squid-dark'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: loot_table
            value: 'fishing/treasure'
```

## Explosions
Want to have some fun?  Cause an explosion!  You can configure the explosion power and whether or not the explosion damages blocks or creates fire.  The `fire` and `break-blocks` parameters are optional and will default to `false` and `true` respectively, while `power` indicates the strength of the explosion.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:bee'
  - 'bee-angry'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: explosion
            power: 5
            fire: false
            break-blocks: true
```

## Sounds
Notify players of special loot being generated!  This item type is capable of playing sounds of any volume, pitch, category, and can even play custom sounds from resource packs!  You can find a list of valid sound values [here](https://www.digminecraft.com/lists/sound_list_pc.php).  `volume` and `pitch` will default to `1`, `category` will default to `master` (values can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/SoundCategory.html)), and `player-only` will default to `true` if not provided.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:axolotl'
  - 'axolotl-variant:blue'
  - 'axolotl-playing-dead'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: sound
            sound: 'entity.firework_rocket.twinkle'
            volume: 1.0
            pitch: 1.0
            player-only: true
```

## Economy
Want to reward players with money for killing mobs or mining blocks?  Supported economy types are currently `vault`, `treasury`, `playerpoints`, and `tokenmanager`, and `coinsengine`.  For economy plugins that support multiple currencies, provide the currency with the property `currency: coins` for example.  If you would like direct support for another economy plugin, please request it in our Discord server.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:spider'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: economy
            economy: vault
            amount: 12.5
```

## Messages
It is possible to send messages to the player that caused the loot to be generated.  Chat message types include `chat_raw`, `chat`, `hotbar`, `title`, and `subtitle`.  The `title` and `subtitle` types can have 3 optional numerical values (measured in ticks) which all have defaults if not provided.  `fade-in` defaults to 20, `duration` defaults to 60, and `fade-out` defaults to 20.  An optional `broadcast` value can be set to `true` to send the message to all players on the server.  Examples of all message types can be found below.
```yaml
type: LOOT_TABLE
conditions: []
pools:
  0:
    conditions: []
    rolls: 1
    bonus-rolls: 0
    entries:
      0:
        items:
          0:
            type: message
            message-type: chat_raw
            value: '{"text":"Sample chat_raw message","color":"yellow"}'
          1:
            type: message
            message-type: chat
            value: '&eSample chat message. Hello %player%!'
          2:
            type: message
            message-type: hotbar
            value: '&c&o&lSample hotbar message'
          3:
            type: message
            message-type: title
            value: '<r:0.5>Sample title message'
            fade-in: 20
            duration: 60
            fade-out: 20
          4:
            type: message
            message-type: subtitle
            value: '<g:#ff00ff:#00ffff>Sample subtitle message'
            fade-in: 20
            duration: 60
            fade-out: 20
```

## Particles
Make the loot generation a little special with particles!  All particle types are supported, you can find a list of them [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html).  Since particles have so many settings depending on the particle type used, details can be found in a collapsed section below the example provided.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: particle
            particle: end_rod
            amount: 20
            offset-x: 1.0
            offset-y: 1.0
            offset-z: 1.0
            player-only: false
            long-distance: true
```
??? note "Particle Settings"
    | Particle Data Type | Value Name | Valid Values | Description |
    | --- | --- | --- | --- |
    | **All** | `particle` | [Particle](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html) | The type of particle to display |
    |  | `amount` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | The amount of particles to display |
    |  | `offset-x`, `offset-y`, `offset-z` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | The distance to randomly offset the particles between on each axis |
    |  | `extra` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | An extra value normally used for particle random movement, does not work for all particle types |
    |  | `player-only` | `true` or `false` | If the particles should only be displayed to the player who caused the loot generation |
    |  | `long-distance` | `true` or `false` | If the particles should be visible from any distance.  Only applies if `player-only` is `false` |
    | **DustOptions** | `red`, `green`, `blue` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) value between 0-255 | The display color values of the `REDSTONE` particles |
    |  | `size` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | How large the particles should be displayed.  The normal `REDSTONE` particle size is 1 |
    | **DustTransition** | All values from **DustOptions** plus `red-fade`, `green-fade`, and `blue-fade` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | The color values to fade `DUST_COLOR_TRANSITION` particles to |
    | **ItemStack** and **BlockData** | `material` | [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) | The item/block to display as the particle texture |
    | **Vibration** | `time` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | How long to display the particles for |
    | **Integer** | `delay` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | How many ticks to wait before the particle animation begins |
    | **Float** | `rotation` | [Number Provider](https://github.com/Rosewood-Development/RoseLoot/wiki/Number-Providers) | A rotation (in radians) for the particle texture |

## Fireworks
Fireworks can be spawned to show that rare or special loot has been dropped.  This follows the same format as [Firework Effect Meta](item-meta.md#firework-effect-meta) with a couple extra options.  `power` can be set to a value between -1 and 127, with a negative value making the firework explode instantly.  The firework can be set to not deal damage by setting `deal-damage: false`.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:wither'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: firework
            power: 1
            deal-damage: false
            flicker: true
            trail: true
            shape: ball_large
            colors:
              - '#FF00FF'
              - 'orange'
            fade-colors:
              - 'red'
              - '#00FFFF'
```

## Potion Effects
Potion effects can be applied to the looter using the same options as the `custom-effects` section of [Potion Meta](item-meta.md#potion-meta).
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:spider,cave_spider'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: potion_effect
            custom-effects:
              0:
                effect: poison
                duration: 100
                amplifier: 1
                ambient: false
                particles: true
                icon: true
```

## Change Tool Durability
Allows adding or removing durability from a tool.  `amount` is a number provider, negative values will damage the tool, positive values will repair it.  Setting `ignore-unbreaking` to `true` will make the tool take damage, ignoring the unbreaking enchantment.  The below example damages a hoe when used to break crops and drops a piece of bonemeal with it.
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'required-tool:hoe'
  - 'block-type:#crops'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: change_tool_durability
            amount: -1
            ignore-unbreaking: false
          1:
            type: item
            item: bone_meal
            amount: 1
```

## Random Number
Allows generating a random number for use with multiple other items. Useful for random numbers in commands and displaying the amount to the player. Placeholders will be generated depending on the `id` of the random number and will be formatted like the following: `%random_number_<id>_int%` for whole numbers and `%random_number_<id>_double%` for fractional values.
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'chance:0.5%'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: random_number
            id: 'coins'
            number:
              min: 10
              max: 30
          1:
            type: command
            value: 'coins give %player% %random_number_coins_int%'
          2:
            type: message
            message-type: chat
            value: '&6While mining, you find %random_number_coins_int%' coins!'
```

## Discord Webhook
You can send a message to a Discord channel using a webhook with this item. The `avatar-url` and `username` may be optionally overridden. Make sure to change the `url` to the correct channel in your server.
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'chance:0.01%'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: discord_webhook
            url: 'https://discord.com/api/webhooks/1065114614492336844/BNRsvM2637vNmH2uJOnh8rnLBthA2hecHDAaWQjal3DlHuI82VSjbyd9rehsWQljuLx1'
            content: '**%player%** found a super rare drop!'
            avatar-url: 'https://avatars.githubusercontent.com/u/54599701?s=200&v=4'
            username: 'RoseLoot Rare Drops'
          1:
            type: item
            item: nether_star
            amount: 1
          2:
            type: message
            message-type: chat
            value: '&6You found a super rare drop!'
```

## RoseStacker Items
[RoseStacker](https://www.spigotmc.org/resources/82729/) items can be dropped on the ground.  `item` determines which type of stacked item to drop, valid types include `spawner`, `spawn_egg`, and `block`.  `stack-type` is the stack type for the item type being dropped.  For `spawner` and `spawn_egg` this would be a mob type, and for `block` the block type.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:zombie'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: rosestacker_stacked_item
            item: spawner
            stack-type: 'zombie'
            stack-size: 1
            amount: 1
```

## MMOCore Experience
[MMOCore](https://www.spigotmc.org/resources/70575/) experience can be granted to a player for either a profession's experience or global experience. The `profession` value is optional and will apply globally if not provided.
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'block-type:#logs'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: mmocore_experience
            profession: foraging
            amount: 1
```

## EcoSkills Experience
[EcoSkills](https://www.spigotmc.org/resources/95541/) experience can be granted to a player for a skill.  Experience is given naturally by default, it can be changed to be given directly by setting `give-naturally: false`. 
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'block-type:#logs'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: ecoskills_experience
            skill: woodcutting
            give-naturally: true
            amount: 1
```

## SCore Variables
[SCore](https://modrinth.com/plugin/score) variables can be set or modified for either a player or globally.  `global` defaults to `false`.  `variable` needs to be set to a valid SCore variable name.  Set `amount` if you are modifying a numerical variable, and use `value` if you are modifying/setting a string variable.  If using `value`, an additional optional `set` property (which defaults to `false`) is available to set the value instead of modify it.
```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'block-type:#logs'
pools:
  0:
    entries:
      0:
        items:
          0: # Using `amount` to add to a numerical variable
            type: score_variable
            variable: woodcutting
            global: false
            amount:
              min: 1
              max: 3
          1: # Using `value` to set a string variable
            type: score_variable
            variable: last_broken_block
            global: false
            set: true
            value: 'log'
```