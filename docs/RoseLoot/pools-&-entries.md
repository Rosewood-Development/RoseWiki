## Introduction
`pools` are the first layer within the loot tables, and `entries` are the next layer within pools.  If you haven't read up on how to create basic loot tables yet, please see the [Overview](overview.md). 

## Configuration
Let's go over how to use all the different options that loot pools and entries offer.  The following is a loot table with all the available pool and entry settings; please note that every single one of them is optional.  
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions:
      - 'killed-by:player'
    rolls:
      min: 1
      max: 3
    bonus-rolls: 0
    entries:
      0:
        weight: 19
        quality: -1
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount: 1
      1:
        weight: 1
        quality: 1
        conditions: []
        items:
          0:
            type: item
            item: emerald_block
            amount: 1
  1:
    conditions:
      - '!killed-by:player'
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: bone
            amount:
              min: 1
              max: 3
```
A loot table may contain any number of pools.  Each pool will be executed as long as the conditions at the top of the loot table are met along with the pool conditions.  This example contains two pools: one pool that runs when a villager is killed by a player, and another that runs when a villager is killed by something other than a player.

The first pool contains entries named `rolls` and `bonus-rolls`.  Both of these have to do with randomly picking entries from the `entries` value.  The `rolls` value determines how many entries will be picked in total.  Rolls do not exclude the entry once it picks one, so it is possible to pick the same entry multiple times over.

`bonus-rolls` is how many extra rolls to add per each level of the player's luck value.  The luck value is determined by either the Luck potion effect, Luck attribute, or Luck of the Sea enchantment (for FISHING loot tables only).  You will likely not need to take advantage of the `bonus-rolls` setting, but it exists if you want to use it.

To determine which entries to pull from, each entry may contain a `weight` value.  Entries with a higher weight have a higher chance of being chosen from the pool.  An entry's chance of being picked is calculated by adding up all total weights and dividing the entry's weight by the total.  In the first pool example given, the first entry has a 19/20 chance of being picked, with the second entry having a 1/20 chance.  If an entry does not contain a weight, it will always be executed a single time regardless of the number of rolls specified on the pool.  If an entry's conditions are not met, the entry will be excluded from the roll entirely.

Similar to the `bonus-rolls` setting, the `quality` setting will change the `weight` of an entry based on the player's current luck value.  This setting is mostly used for fishing with the Luck of the Sea enchantment, but can also be used in other cases.  The weight will be offset by the following formula: `weight = weight + round(quality * luck)`.

I know that was a lot of information to take in at once and it might sound a bit cryptic.  If you need more explanation on something feel free to [join our Discord server](https://discord.gg/MgUsTBK) and ask for additional help.  We will be glad to answer any questions you have. 

## Child Entries
Entries are capable of containing child entries which can be executed using different strategies.  See below for an example that recreates the vanilla loot table for coal ore:
```yaml
type: BLOCK
overwrite-existing: items
conditions:
  - 'block-type:coal_ore'
pools:
  0:
    conditions: []
    rolls: 1
    bonus-rolls: 0
    entries:
      0:
        conditions: []
        children-strategy: first_passing
        children:
          0:
            conditions:
              - 'enchantment:silk_touch,1'
            items:
              0:
                type: item
                item: coal_ore
          1:
            conditions: []
            items:
              0:
                type: item
                item: coal
                enchantment-bonus:
                  formula: ore_drops
                  enchantment: fortune
```
Possible strategies include `normal`, `first_passing`, and `sequential`.  `normal` will execute all the children the same way that entries are normally handled.  `first_passing` will keep trying to execute each child entry until one of them passes all conditions, and then it stops.  `sequential` is the opposite of `first_passing`, it will continue executing each child entry until one of them does not pass, and then will stop.