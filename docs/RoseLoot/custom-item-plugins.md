## Introduction
Are you using a custom items plugin and want to drop some custom items?  If so, this is the place for you.  Custom items support the same parameters as [Items](item-types.md).  If you would like direct support for another custom items plugin, please request it in our Discord server.  You can find examples of how to drop items from these plugins below.

## [CustomItems](https://www.spigotmc.org/resources/63848/)/[ItemBridge](https://www.spigotmc.org/resources/77080/)
If you wish to drop items from the CustomItems plugin, you must also have [ItemBridge](https://www.spigotmc.org/resources/77080/) installed.  To drop an item from CustomItems, prefix the item ID with `cui:`.

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
            type: custom_item
            plugin: itembridge
            item: 'cui:emeraldHoe'
            amount: 1
```

## [ItemEdit](https://www.spigotmc.org/resources/40993/)
Use the item ID that is saved in server storage.

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
            type: custom_item
            plugin: itemedit
            item: 'youritem'
            amount: 1
```

## [ItemsXL](https://www.spigotmc.org/resources/14472/)
The item ID will be the .yml file name of the item.

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
            type: custom_item
            plugin: itemsxl
            item: 'your_item'
            amount: 1
```

## [UberItems](https://spigotmc.org/resources/64923/)
The item ID will be the ID of the UberItem or UberMaterial as defined in the plugin or addon.

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
            type: custom_item
            plugin: uberitems
            item: 'your_item'
            amount: 1
```

## [ItemsAdder](https://www.spigotmc.org/resources/73355/)
Simply use the item ID as defined in the ItemsAdder configs.  Some item IDs may require a prefix if they are added by an expansion.

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
            type: custom_item
            plugin: itemsadder
            item: 'ruby_ore'
            amount: 1
```

## [MythicMobs](https://www.spigotmc.org/resources/5702/)
Simply use the item name as defined in the MythicMob item configs.

```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
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
            type: custom_item
            plugin: mythicmobs
            item: 'SkeletonKingSword'
            amount: 1
```

## [MMOItems](https://www.spigotmc.org/resources/39267/)
The `item` field must contain a `:` which separates the item type and the item ID.  This field is case-sensitive, meaning it must match the item type and item ID exactly how it is in the MMOItems configs.

```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
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
            type: custom_item
            plugin: mmoitems
            item: 'BOW:MARKING_BOW'
            amount: 1
```

## [Knokko's CustomItems](https://www.spigotmc.org/resources/88182/)
The item ID will be the name of the item you defined in the editor.

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
            type: custom_item
            plugin: knokkocustomitems
            item: 'your_item'
            amount: 1
```

## [Oraxen](https://www.spigotmc.org/resources/72448/)
The item ID will be the name of the item in the .yml file.

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
            type: custom_item
            plugin: oraxen
            item: 'bedrock_pickaxe'
            amount: 1
```

## [ExecutableItems](https://www.spigotmc.org/resources/77578/)
Simply use the item ID as defined in the ExecutableItems configs.

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
            type: custom_item
            plugin: executableitems
            item: 'world_teleporter'
            amount: 1
```

## [ExecutableBlocks](https://www.spigotmc.org/resources/93406/)
Simply use the block ID as defined in the ExecutableBlocks configs.

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
            type: custom_item
            plugin: executableblocks
            item: 'Free_Test'
            amount: 1
```

## [Eco](https://github.com/Auxilor/eco)
The `item` field supports any item ID that Eco normally would.  Examples for Eco-supported plugins include `ecoitems:enchanted_ender_eye`, `ecoarmor:shard_angelic`, and `ecobosses:steel_golem_spawn_egg`.

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
            type: custom_item
            plugin: eco
            item: 'ecoitems:enchanted_ender_eye'
            amount: 1
```

## [Slimefun](https://github.com/Slimefun/Slimefun4)
Use the item ID as defined by Slimefun or an addon.

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
            type: custom_item
            plugin: slimefun
            item: 'fortune_cookie'
            amount: 1
```

## [CustomCrafting](https://www.spigotmc.org/resources/55883/)
Use the namespaced key formatted like `PluginName:folder/itemID`.

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
            type: custom_item
            plugin: customcrafting
            item: 'customcrafting:customcrafting/recipe_book'
            amount: 1
```

## [CustomFishing](https://polymart.org/resource/customfishing.2723)
The item format goes as follows: `category:name`.  Available categories include `bait`, `hook`, `item`, `rod`, and `util`.

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
            type: custom_item
            plugin: customfishing
            item: 'bait:worm_bait'
            amount: 1
```

## [AdvancedItems](https://www.spigotmc.org/resources/110438/)
Use the item ID as defined by the config files.

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
            type: custom_item
            plugin: advanceditems
            item: 'emerald_scythe'
            amount: 1
```

## [zEssentials](https://www.spigotmc.org/resources/118014/)
Use the item ID as defined by the config files.

```yaml
type: ENTITY
overwrite-existing: none
conditions:
  - 'entity-type:iron_golem'
  - 'spawn-reason:spawner'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: custom_item
            plugin: zessentials
            item: 'ancient_poppy'
            amount:
              min: 1
              max: 2
            enchantment-bonus:
              enchantment: looting
              bonus-per-level:
                min: 0
                max: 1
```

## [zItems](https://www.spigotmc.org/resources/118638/)
Use the item ID as defined by the config files.

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
            type: custom_item
            plugin: zitems
            item: 'shiny_emerald'
            amount: 1
```

## [Nexo](https://polymart.org/resource/nexo.6901)
The item ID will be the name of the item in the .yml file.

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
            type: custom_item
            plugin: nexo
            item: 'sapphire_pickaxe'
            amount: 1
```

## [CrazyVouchers](https://modrinth.com/plugin/crazyvouchers)
The item ID is the voucher name.

```yaml
type: BLOCK
overwrite-existing: none
conditions:
  - 'block-type:#diamond_ores'
  - 'chance:0.1%'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: custom_item
            plugin: crazyvouchers
            item: 'your_voucher'
            amount: 1
```

## [CraftEngine](https://modrinth.com/plugin/craftengine)
The item ID is used as defined in the pack configuration files.

```yaml
type: BLOCK
overwrite-existing: items
conditions:
  - 'craftengine-block:default:chinese_lantern'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: custom_item
            plugin: craftengine
            item: 'default:topaz'
            amount: 1
```
