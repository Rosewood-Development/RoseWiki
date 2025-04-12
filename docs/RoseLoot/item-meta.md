## Introduction
This is a continuation of the item type section, please read that first if you haven't. 

## Normal Meta
These values will apply to every item that can be dropped.  All values are optional.

| Value Name | Type | Description |
| --- | --- | --- |
| `amount` | Whole number | The amount of items that will drop.  See [Number Providers](number-providers.md) for more info. |
| `max-amount` | Whole number | If `amount` is higher than this value, it will be set to this value. |
| `display-name` | Text | The name of the item, supports color codes. |
| `lore` | List of text | The lore of the item, supports color codes and multiple values. |
| `custom-model-data` | Whole number | The custom model data of an item.  Used for resource packs.  If you don't know what this is, you probably don't need it. |
| `unbreakable` | `true` or `false` | Whether or not the item can take damage.  Mainly only applies to items that can take damage. |
| `repair-cost` | Positive whole number | The cost in levels of the next repair in an anvil.  Mainly only applies to items that can be repaired. |
| `durability` | A whole number or percentage | The durability of the item.  Mainly only applies to items that have durability.  Should not be included if `min-durability` and `max-durability` are used. |
| `min-durability` and `max-durability` | A whole number or percentage | Same as `durability`, must include both values.  Should not be included if `durability` is used. |
| `hide-flags` | List of [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html) or `true` | Allows hiding certain text in the item description.  If set to `true`, all applicable item flags will be hidden. |
| `copy-block-state` | `true` or `false` | Only applies to loot tables of type `BLOCK`.  Allows copying the tile entity state of the block that was broken into the item. |
| `copy-block-data` | `true` or `false` | Only applies to loot tables of type `BLOCK`.  Allows copying the block data of the block that was broken into the item. |
| `copy-block-name` | `true` or `false` | Only applies to loot tables of type `BLOCK`.  Allows copying the name of the block container that was broken onto the item. |
| `smelt-if-burning` | `true` or `false` | Only applies to loot tables of type `ENTITY`.  Smelts the resulting item if the looted entity is on fire. |
| `loot-table` | The key of a loot table installed on your server, either through vanilla or a datapack | Only applies to items that are considered Lootable, such as containers or suspicious sand. |
| `restore-vanilla-attributes` | `true` or `false` | Enabled by default, restores vanilla attributes to items on 1.21+. |
| `looter-pickup-only` | `true` or `false` | If true, only the looting player will be able to pick up this item. |

#### Randomly Applied Enchantments
An item can have random enchantments applied.  The following is an example.
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
            type: item
            item: diamond_sword
            amount: 1
            enchant-randomly:
              level: 30
              treasure: true
```
The `level` value is the enchantment table equivalent of the enchantments that will be put onto the item.  `treasure` determines if enchantments such as `mending` can be applied to the item.

#### Random Enchantment
This differs from the above section as this only applies a single enchantment with a randomly chosen level.  If you set `random-enchantments: []` it will pick from every applicable enchantment for the item.
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
            type: item
            item: diamond_sword
            amount: 1
            random-enchantments:
              - sharpness
              - smite
              - bane_of_arthropods
```

#### Enchantments
If you don't want random enchantments, you can specify the exact enchantments you want instead.
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
            type: item
            item: diamond_sword
            amount: 1
            enchantments:
              sharpness: 5
              looting: 3
```
You can find a list of all enchantments [here](https://www.digminecraft.com/lists/enchantment_list_pc.php).

#### Enchantment Bonus
If you want to increase the number of a specific item that can drop when using an enchantment such as looting, you can do that with this section.
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
            type: item
            item: emerald
            amount: 1
            enchantment-bonus:
              formula: uniform
              enchantment: looting
              bonus-per-level: 1
```
`enchantment` is which enchantment type will increase the drop chance.  You can find a list of all enchantments [here](https://www.digminecraft.com/lists/enchantment_list_pc.php).  `formula` determines which formula to use for calculating the item bonus.  Valid formula values are `uniform`, `binomial`, and `ore_drops`.  Information on each formula type and their individual options can be found below:

??? note "Enchantment Bonus Formulas"

    #### Uniform
    Requires a number parameter `bonus-per-level` which is the number of extra items possible per enchantment level.

    #### Binomial
    Requires a number parameter `bonus-per-level` which is the number of extra items possible for each passing chance, and `probability` between 0 and 1 which is the chance of the adding the `bonus-per-level` items per enchantment level.

    #### Ore Drops
    Requires no extra parameters.  This is the formula used for vanilla ore drops.  Extra items = `amount * (max(0; random(0..Level + 2) - 1) + 1)`

#### Amount Modifiers
It is possible to alter the amount of items to drop based on a list of conditions.  `conditions` is the list of conditions which function identically to how other condition fields work.  `value` determines the amount of the modifier.  `add` determines how the `value` should be applied to the original amount; if `true` the `value` will be added to the amount, and if `false` the amount will be set to the `value`.  Below is the vanilla loot table for cocoa beans as an example:
```yaml
type: BLOCK
overwrite-existing: items
conditions:
  - 'block-type:cocoa'
pools:
  0:
    conditions: []
    rolls: 1
    bonus-rolls: 0
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: cocoa_beans
            amount: 1
            amount-modifiers:
              0:
                conditions:
                  - 'block-data:age=2'
                value: 3
                add: false
```

#### Attribute Modifiers
If you want to make the dropped items do some crazy stuff, you can add attribute modifiers to them.  This is a fairly complex feature, so just be warned.
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
            type: item
            item: diamond_sword
            amount: 1
            attributes:
              0:
                name: 'generic.max_health'
                amount: 20
                operation: add_number
                slot: hand
```
As you can see, you are able to add multiple attribute modifiers.  To add more, just add another entry under attributes.

`name` is the name of the attribute; valid names can be found [here](https://minecraft.wiki/w/Attribute).  `amount` is the value of the attribute.  In the case of `generic.max_health` here, it is the amount of health to increase by.  The value of `20` means 20 health, which is 10 additional hearts.

`operation` is a bit complicated to understand.  The valid values are `add_number`, `add_scalar`, and `multiply_scalar_1`.  `add_number` will add to the existing value.  `add_scalar` will multiply all other modifiers by the amount.  `multiply_scalar_1` will add the base value multiplied by the amount specified.

`slot` determines when the attribute modifier will be applied.  Valid values can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/EquipmentSlot.html).  If no slot is specified, it will apply for all slots.

## NBT Data
Custom NBT can be written to items by using the `nbt` option with a valid NBT string.  Note: This requires the [NBT API](https://www.spigotmc.org/resources/7939/) plugin to be installed.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:villager'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: emerald
            nbt: '{MyCustomNBTValue:"A custom NBT value on an emerald!"}'
```

## Axolotl Bucket Meta
Applicable to `axolotl_bucket` items.  `variant` allows changing what color of axolotl will spawn from the bucket.  Valid values can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Axolotl.Variant.html).  `copy-looted` can be `true` or `false`, if it's `true` and the loot table type is `ENTITY` and the killed entity was an axolotl, the axolotl type will be copied into the bucket. 
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:axolotl'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: axolotl_bucket
            amount: 1
            variant: blue
            copy-looted: false
```

## Banner Meta
Applicable to all `banner` items.  You may specify a list of patterns and provide the `color` and `pattern` (type) for each pattern.  Valid colors can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/DyeColor.html) and valid pattern types can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html).
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: white_banner
            amount: 1
            patterns:
              0:
                color: red
                pattern: rhombus_middle
              1:
                color: blue
                pattern: flower
```

## Written Book Meta
Applicable to `writable_book` items.  You may specify the book `title`, `author`, `pages` (page content), and `generation` (how the book was created).

`title` and `author` are both text values that do not support color codes, `pages` is a text list that supports color codes, and `generation` values can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/meta/BookMeta.Generation.html).
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: written_book
            amount: 1
            title: 'Book of Mysteries'
            author: 'A Lost Soul'
            pages:
              - '<r:0.5>The first page with super magical rainbow colored text!'
              - 'The boring second page with default colored text.'
            generation: tattered
```

## Enchantment Storage Meta
Applicable to `enchanted_book` items.  Functions identically to [applying enchantments to a normal item](item-meta.md#enchantments), except they will be added as enchantments stored in the enchanted book instead.

## Firework Effect Meta
Applicable to `firework_star` items.  This is not for the actual firework items, just for the star.

`flicker` can be `true` or `false` and determines if the firework will flicker.  `trail` can be `true` or `false` and determines if the firework particles will leave a trail behind them.  `shape` determines the shape of the firework; valid types can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html).  `colors` is a list of colors that the particles will be, and it can contain color names or hex codes.  `fade-colors` functions the same as `colors`, except it will be the color the particles fade to over their lifetime.  A list of valid firework color names can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html).
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: firework_star
            amount: 1
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

## Firework Meta
Applicable to `firework_rocket` items.  Determines what power and effects a firework rocket will have.  The `power` value will determine how far up the firework flies; the normal craftable range is between 1 and 3, but higher values can be used.  The `firework-effects` section functions identically to how it does in [Firework Effect Meta](item-meta.md#firework-effect-meta), but is provided as a list.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: firework_rocket
            amount: 1
            power: 2
            firework-effects:
              0:
                flicker: true
                trail: true
                type: large_ball
                colors:
                  - '#FF00FF'
                  - 'orange'
                fade-colors:
                  - 'red'
                  - '#00FFFF'
```

## Knowledge Book Meta
Applicable to `knowledge_book` items.  Allows you to configure what recipes a knowledge book will unlock when used.  You may provide a `recipes` list using the [internal recipe IDs](https://mcreator.net/wiki/list-vanilla-recipe-registry-names), or you may leave the value off entirely.  If no `recipes` list is provided, the knowledge book will unlock all recipes. 
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: knowledge_book
            amount: 1
            recipes:
              - 'beacon'
              - 'bone_meal_from_bone_block'
              - 'white_dye_from_lily_of_the_valley'
```

## Leather Armor Meta
Applicable to leather armor items (`leather_helmet`, `leather_chestplate`, `leather_leggings`, `leather_boots`).  Allows the ability to `color` the armor using hex codes.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: leather_chestplate
            amount: 1
            color: '#C0FFEE'
```

## Armor Trim Meta
Applicable to any armor item that allows applying trims.  Trim materials must be a [TrimMaterial](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/meta/trim/TrimMaterial.html).  Trim patterns must be a [TrimPattern](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/meta/trim/TrimPattern.html).
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: netherite_chestplate
            amount: 1
            trim:
              material: amethyst
              pattern: silence
```

## Potion Meta
Applicable to `potion`, `splash_potion`, and `lingering_potion` items.  This is by far the most complex item meta type, so be warned.

`color` determines the color of the potion; this must be a hex code.  `potion-type` is the main effect of the potion; values can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionType.html).  Note: Do not use any value names ending in _STRONG, they will not work.  Use an `upgraded` value of `true` as seen below for level 2 potions.

`upgraded` can be `true` or `false` and determines if the potion has had glowstone added to it in a brewing stand; setting it to `true` makes it level 2.  `extended` can be `true` or `false` and determines if the potion has had redstone added to it in a brewing stand; setting it to `true` makes it have a longer effect duration.

`custom-effects` allows you to configure additional effects for the potion.  `effect` is the potion effect type.  The `effect` is not the same as the previous `potion-type` and uses different values that can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html).  `duration` is the duration in ticks.  `amplifier` is the level of the effect plus 1; if the amplifier is 1, the effect level will be 2.

`ambient` can be `true` or `false`; if `true`, the particles given off by this effect will be transparent.  `particles` can be `true` or `false`; if `false`, no particles be will given off by this effect.  `icon` can be `true` or `false`; if `true`, an icon for the effect will appear in the corner of the player's screen.  `overwrite` can be `true` or `false`; if `true`, it will overwrite any existing effects of the same type on the player when applied.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: splash_potion
            amount: 1
            color: '#FF0000'
            potion-type: instant_damage
            upgraded: true
            extended: false
            custom-effects:
              0:
                effect: regeneration
                duration: 100
                amplifier: 1
                ambient: false
                particles: true
                icon: true
                overwrite: true
              1:
                effect: luck
                duration: 100
                amplifier: 0
                ambient: true
                particles: true
                icon: true
                overwrite: true
```

## Player Head Meta
Applicable to `player_head` items.  Only one value out of all of the ones listed here can be used.  If you use multiple, only one will be applied.

`texture` is the Base64 texture string for the head to use; you can find an example value [here](https://minecraft-heads.com/custom-heads/miscellaneous/43868-rose#UUID-Value).  `owner` can be a player UUID or name.  `hdb-id` uses a head ID and will only work when the plugin [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) is installed.  There are two additional values of `copy-looted` and `copy-looter`, both of which accept either `true` or `false` values; if `true`, they will copy the player's head for the looted entity (if a player) and looter (if a player) respectively.  `copy-looted` only works for loot tables with a type of `ENTITY`.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: player_head
            amount: 1
            owner: '27f49f81-0a43-445b-8d82-246badecf358'
```

## Suspicious Stew Meta
Applicable to `suspicious_stew` items.  This functions almost identically to the additional effects in the [Potion Meta](item-meta.md#potion-meta).  If `pick-random-effect` is optionally set to `true`, it will pick a single random effect from the `custom-effects` list.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: suspicious_stew
            amount: 1
            pick-random-effect: false
            custom-effects:
              0:
                effect: regeneration
                duration: 100
                amplifier: 1
                ambient: false
                particles: true
                icon: true
                overwrite: true
```

## Tropical Fish Bucket Meta
Applicable to `tropical_fish_bucket` items.  `body-color` allows changing the body color of the fish; valid values can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html).  `pattern-color` allows changing the color of the pattern of the fish; the same values are allowed as `body-color`.  `pattern` determines the pattern on the fish; valid values can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/TropicalFish.Pattern.html).  The value of `copy-looted` can be `true` or `false`; if true and the loot table type is `ENTITY` and the looted entity is a tropical fish, the properties of the fish will be copied into the bucket.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: tropical_fish_bucket
            amount: 1
            body-color: white
            pattern: stripey
            pattern-color: orange
```

## Bundle Meta
Applicable to `bundle` items.  As of 1.17, bundles now exist in the game and can be filled with pretty much anything, including other bundles.  You can use a list of valid loot items as the `contents` of the bundle.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:pig'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: bundle
            amount: 1
            display-name: '&dLoot Bag'
            contents:
              0:
                type: item
                item: diamond
                amount:
                  min: 1
                  max: 3
              1:
                type: item
                item: emerald
                amount:
                  min: 1
                  max: 3
```

## Exploration Map Meta
Applicable to `map` items.  `destination` determines what feature the map will navigate towards; valid values can be found [here](https://minecraft.wiki/w/Commands/locate#Arguments).  `scale` allows the zoom of the map to be changed; valid values can be found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/map/MapView.Scale.html).  `search-radius` determines how many chunks away from the loot generation location to check for a structure with the same type as the `destination`; must be whole number greater than or equal to 0.  `skip-known-structures` determines if additional chunks can be generated to locate the desired destination type and can be `true` or `false`.
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
            type: item
            item: map
            destination: pillager_outpost
            search-radius: 100
            skip-known-structures: false
            scale: farthest
            amount: 1
```

## Music Instrument Meta
Applicable to `goat_horn` items.  `music-instrument` allows setting the [Music Instrument](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/MusicInstrument.html) of the goat horn.
```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:goat'
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: goat_horn
            music-instrument: dream_goat_horn
            amount: 1
```

## Food Component
Allows turning any item into food!  Only available in 1.21+.  All properties are optional and will be filled with default properties if not given.  `nutrition` sets how much hunger to restore.  `saturation` sets how much saturation to apply.  `eat-seconds` is the number of seconds (allows decimals) that the item must be held down for to be eaten.  `can-always-eat` can be set to either `true` or `false`, if true the item will be able to be eaten even with a full hunger bar.  `convert-to-item` can be set to any [Loot Item](item-types.md) that drops a single item stack.  `effects` is a list of probabilities and [potion effects](item-meta.md#potion-meta) to be applied after eating the item.
```yaml
type: LOOT_TABLE
conditions: []
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: diamond
            amount: 1
            food-component:
              nutrition: 6
              saturation: 10
              eat-seconds: 1.5
              can-always-eat: true
              convert-to-item:
                type: item
                item: emerald
                amount: 1
              effects:
                0:
                  probability: 0.5
                  effect: regeneration
                  duration: 100
                  amplifier: 1
                  ambient: false
                  particles: true
                  icon: true
```

## Tool Component
Allows turning any item into a tool!  Only available in 1.21+.  `default-mining-speed` is the speed that the tool will mine all blocks that are not included in the rules list, 1.0 is the default mining speed.  `damage-per-block` is the amount of damage to apply to the item per block mined.  `rules` is a list of blocks that the tool uses to determine how fast to mine blocks and if the blocks should drop items.  The rule `speed` overwrites the `default-mining-speed` and `correct-for-drops` can be set to `true` or `false` to determine if the block being broken should drop items.  The rule `blocks` can either be any [block tag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Tag.html) or a list of block names. 
```yaml
type: LOOT_TABLE
conditions: []
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: diamond
            amount: 1
            tool-component:
              default-mining-speed: 1.0
              damage-per-block: 1
              rules:
                0:
                  speed: 4
                  correct-for-drops: true
                  blocks:
                    - '#wool'
                1:
                  speed: 10
                  correct-for-drops: true
                  blocks:
                    - 'stone'
                    - 'deepslate'
```

## Jukebox Playable Component
Allows turning any item into a music disc!  Only available in 1.21+.  `song` can be set to any music disc name, such as `11`, `cat`, `precipice`, etc.  `show-in-tooltip` can be set to `true` or `false` and determines if the song name should be shown in the item's description.
```yaml 
type: LOOT_TABLE
conditions: []
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: diamond
            amount: 1
            jukebox-playable-component:
              song: 'precipice'
              show-in-tooltip: true
```