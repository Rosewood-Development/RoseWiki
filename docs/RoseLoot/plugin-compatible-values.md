## Introduction
If you would like to check for certain conditions regarding other plugins, you can find examples of those conditions below.  These conditions are used in the same way as other conditions, and you can visit the [Generic Values](generic-values.md) page to learn more about them.

## Checking NBT Values
Requires the [NBT API](https://www.spigotmc.org/resources/7939/) plugin to be installed to use.  These conditions take an NBT path and compare the value at that path with a specified value.  To access an array in an NBT path, put `[n]` at the end of the path value where `n` is the array index.  An example of how to use this to check a player head texture can be seen in the first row of the table below.  Valid operators include one of the following: `!=`, `<=`, `>=`, `=`, `<`, `>`, `^` (contains).

| Condition | Description | Example |
| --- | --- | --- |
| `nbt-block` | Allows checking the NBT of a placed tile entity. | `nbt-block:SkullOwner.Properties.textures[0].Value^mY4ZTFmOTQzZWQ5ZDUxYmUwM2IwNyJ9fX0` | 
| `nbt-entity` | Allows checking the NBT of a looted entity. | `nbt-entity:LeftHanded=1` |
| `nbt-item` | Allows checking the NBT of the tool used for looting. | `nbt-item:MyCustomNBTValue>=5` |
| `nbt-looter` | Allows checking the NBT of the looting entity. | `nbt-looter:XpTotal<100` | 


## Custom Items Plugin Compatibility
| Plugin | Condition | Example |
| --- | --- | --- |
| [CustomItems](https://www.spigotmc.org/resources/77578/)/[ItemBridge](https://www.spigotmc.org/resources/77080/) | `itembridge-type` | `itembridge-type:cui:emeraldHoe` |
|  | `itembridge-inventory-contains` | `itembridge-inventory-contains:emeraldHoe,1` |
| [ItemsXL](https://www.spigotmc.org/resources/14472/) | `itemsxl-type` | `itemsxl-type:your_item` |
|  | `itemsxl-inventory-contains` | `itemsxl-inventory-contains:your_item,3` |
| [ItemsAdder](https://www.spigotmc.org/resources/73355/) | `itemsadder-type` | `itemsadder-type:ruby_ore` |
|  | `itemsadder-inventory-contains` | `itemsadder-inventory-contains:ruby_ore,3` |
| [MythicMobs](https://www.spigotmc.org/resources/5702/) | `mythicmobs-item-type` | `mythicmobs-item-type:SkeletonKingSword` |
|  | `mythicmobs-inventory-contains` | `mythicmobs-inventory-contains:SkeletonKingSword,1` |
| [MMOItems](https://www.spigotmc.org/resources/39267/) | `mmoitems-type` | `mmoitems-type:BOW:MARKING_BOW` |
|  | `mmoitems-inventory-contains` | `mmoitems-inventory-contains:BOW:MARKING_BOW,1` |
| [Knokko's CustomItems](https://www.spigotmc.org/resources/88182/) | `knokkocustomitems-type` | `knokkocustomitems-type:your_item` |
|  | `knokkocustomitems-inventory-contains` | `knokkocustomitems-inventory-contains:your_item,3` |
| [Oraxen](https://www.spigotmc.org/resources/72448/) | `oraxen-type` | `oraxen-type:bedrock_pickaxe` |
|  | `oraxen-inventory-contains` | `oraxen-inventory-contains:bedrock_pickaxe,1` |
| [ExecutableItems](https://www.spigotmc.org/resources/63848/) | `executableitems-type` | `executableitems-type:world_teleporter` |
|  | `executableitems-inventory-contains` | `executablkeitems-inventory-contains:world_teleporter,1` |
| [EcoItems](https://www.spigotmc.org/resources/94601/) | `ecoitems-type` | `ecoitems-type:ecoitems:enchanted_ender_eye` |
|  | `ecoitems-inventory-contains` | `ecoitems-inventory-contains:enchanted_ender_eye,3` |
| [SlimeFun](https://github.com/Slimefun/Slimefun4) | `slimefun-type` | `slimefun-type:fortune_cookie` |
|  | `slimefun-inventory-contains` | `slimefun-inventory-contains:fortune_cookie,3` |
| [Nexo](https://polymart.org/resource/nexo.6901) | `nexo-type` | `nexo-type:sapphire_pickaxe` |
|  | `nexo-inventory-contains` | `nexo-inventory-contains:sapphire_pickaxe,1` |
| [CrazyVouchers](https://modrinth.com/plugin/crazyvouchers) | `crazyvouchers-type` | `crazyvouchers-type:voucher_name` |
|  | `crazyvouchers-inventory-contains` | `crazyvouchers-inventory-contains:voucher_name,1` |
| [CraftEngine](https://modrinth.com/plugin/craftengine) | `craftengine-type` | `craftengine-type:default:topaz` |
|  | `craftengine-inventory-contains` | `craftengine-inventory-contains:default:topaz,1` |

## Natural Block Detection Plugins
| Plugin | Condition | Description |
| --- | --- | --- |
| [BlockTracker](https://modrinth.com/plugin/blocktracker) | `blocktracker-natural-block` | The recommended way of checking for natural blocks |
| [CoreProtect](https://www.spigotmc.org/resources/8631/) | `coreprotect-natural-block` | Not recommended, can make database queries on the main thread and cause lag spikes |

## Custom Blocks Plugin Compatibility
| Plugin | Condition | Example |
| --- | --- | --- |
| [ItemsAdder](https://www.spigotmc.org/resources/73355/) | `itemsadder-block` | `itemsadder-block:ruby_ore` |
| [Oraxen](https://www.spigotmc.org/resources/72448/) | `oraxen-block` | `oraxen-block:autumn_leaves` |
| [Nexo](https://polymart.org/resource/6901) | `nexo-block` | `nexo-block:sapphire_ore` |
| [CraftEngine](https://modrinth.com/plugin/craftengine) | `craftengine-block` | `craftengine-block:default:palm_leaves` |

## Custom Biome Plugin Compatibility
If you are using a custom biomes plugin, the regular `biome` condition will not work (Note: This is no longer the case as of 1.21.3!).  You can use the special custom biome conditions below instead.

| Plugin | Condition | Example |
| --- | --- | --- |
| [Terra](https://www.spigotmc.org/resources/85151/) | `terra-biome` | `terra-biome:autumnal_forest` |

## Other Plugin Compatibility Values
| Plugin | Condition | Description | Types | Values | Example |
| --- | --- | --- | --- | --- | --- |
| [RoseStacker](https://www.spigotmc.org/resources/82729/) | `rosestacker-stacked-entity` | Allows checking if an entity is stacked. | ENTITY | None | `rosestacker-stacked-entity` |
|  | `rosestacker-primary-entity` | Allows checking if an entity is the one at the top of a stack. | ENTITY | None | `rosestacker-primary-entity` |
| [MythicMobs](https://www.spigotmc.org/resources/5702/) | `mythicmobs-type` | Allows checking for a MythicMob type.  You will need to set `PreventOtherDrops: false` for the MythicMob type to get the RoseLoot drops to appear properly.  You can prevent the drops by setting `overwrite-existing: items` in the loot table. | ENTITY | A MythicMob type | `mythicmobs-type:SkeletonKing` |
|  | `mythicmobs-entity` | Allows checking if an entity is a MythicMobs entity. | ENTITY | None | `mythicmobs-entity` |
| [EcoMobs](https://www.spigotmc.org/resources/86576/) | `ecomobs-type` | Allows checking for an EcoMobs type. | ENTITY | An EcoMobs type | `ecomobs-type:steel_golem` |
| [EcoBosses](https://www.spigotmc.org/resources/86576/) | `ecobosses-type` | Allows checking for an EcoBosses type. | ENTITY | An EcoBosses type | `ecobosses-type:steel_golem` |
| [RealisticSeasons](https://www.spigotmc.org/resources/93275/) | `realisticseasons-season` | Allows checking if it's a current season in the looted world. | ANY | A season type | `realisticseasons-season:winter` |
|  | `realisticseasons-event` | Allows checking if an event is active in the looted world. | ANY | An event type | `realisticseasons-event:easter` |
