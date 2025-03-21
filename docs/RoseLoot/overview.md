## Introduction
Custom loot is entirely handled through the use of Loot Tables.  You can find some pre-installed loot tables located in the `/plugins/RoseLoot/loottables/examples` directory.  Any loot tables in this examples directory will not be parsed by the plugin.

## Loot Table Types
There are currently multiple different loot table types which can be found in the table below.

| Loot Table Type | Description |
| --- | --- |
| `ENTITY` | Used to edit mob drops and do things when mobs die. |
| `BLOCK` | Used to edit block drops and do things when blocks break. Some features may require [Paper](https://papermc.io/) (primarily crops). |
| `HARVEST` | Used to edit items harvested from right clicking certain blocks. Some features may require [Paper](https://papermc.io/) (primarily shearing pumpkins/bee hives). |
| `FISHING` | Used to edit items that can be acquired through fishing. |
| `CONTAINER` | Used to edit the items that generate from chests generated throughout the world. |
| `PIGLIN_BARTER` | Used to edit the items that piglins can trade gold for. |
| `ENTITY_DROP_ITEM` | Used to edit items that entities drop, such as chickens laying eggs or sheep being sheared.  Not to be confused with `ENTITY`.  Runs once per each item dropped. |
| `ADVANCEMENT` | Used to give loot when a player completes an advancement. |
| `ARCHAEOLOGY` | Used to edit the item within suspicious sand and gravel. |
| `VAULT` | Used to edit the loot dispensed from a Vault or Trial Spawner. |
| `LOOT_TABLE` | An advanced type that allows putting loot tables inside of other loot tables.  Also useful for use with the `/loot generate` command. |

## Basic Configuration
The following sections will be about how to configure your very own loot table.  If you would rather learn by practical example, you can find some located in the `/plugins/RoseLoot/loottables/examples` directory.

To make a new loot table, create a new `.yml` file in the `/plugins/RoseLoot/loottables` directory named whatever you want.  You can (and should) create multiple loot table files in order to stay organized.  The following is the most simplistic type of loot table you can create.  Each of the pieces will be explained in more detail below.
```yaml
type: ENTITY
overwrite-existing: items
conditions: []
pools:
  0:
    entries:
      0:
        items:
          0:
            type: item
            item: emerald
            amount: 1
```
As you can see, this loot table is extremely bare bones and does not contain any of the optional values.  Let's go over the values which are required.

The first is `type`, which defines which type of loot table the file will use.  The possible values of this setting can be found in the table listed at the top of this page.

The next setting is `overwrite-existing` which determines what type of default loot this table will overwrite.  Valid values include `all`, `items`, `experience`, and `none`.  All loot table types can use this setting, other than `LOOT_TABLE` which doesn't use it at all.  If left blank, `overwrite-existing` will default to `none`.  The top level `conditions` setting determines when the loot file will be executed.

Let's continue with the example.  In its current state, it isn't very useful and will drop an emerald for every mob that dies.  We can fix that by adding a condition to make it only drop emeralds for villagers.
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
In addition to having conditions at the top of the file, you may also provide them for each pool and loot entry as well.  Having conditions on a pool or loot entry will require all those conditions to be met in order to include that pool or entry in the loot generation.  As you can see, the conditions are what makes this plugin so powerful.  There are dozens of different conditions for you to pick from to really fine-tune the plugin to do exactly what you want.

To go into more detail about what you can do with each type of loot table, or to see the different options available to use as loot, consult the sidebar of this page.