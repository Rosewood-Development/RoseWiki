## Introduction
Context placeholders will be replaced within text the same way that PlaceholderAPI placeholders are.  You can find a list of all context placeholders available below.  Context placeholders are parsed _before_ PlaceholderAPI placeholders.

### Always Available
These placeholders will always be available and do not require any special conditions.

| Placeholder | Description |
| --- | --- |
| `%world%` | The world the loot was generated in |
| `%world_time_ticks%` | The time of the world in ticks (0-24000) |
| `%x%` | The X coordinate the loot was generated at |
| `%y%` | The Y coordinate the loot was generated at |
| `%z%` | The Z coordinate the loot was generated at |
| `%luck_level%` | The luck level of the looter.  Will be 0 if there is no looter. |

### Conditionally Available

| Placeholder | Description | Requirement |
| --- | --- | --- |
| `%player%` | That player that caused the loot to be generated | A player must have caused the loot to generate |
| `%entity_type%` | The entity type that was looted | An entity must have been looted |
| `%entity_name%` | The name of the entity that was looted | An entity must have been looted |
| `%block_type%` | The block type that was looted | A block must have been looted |
| `%item_type%` | The item used to loot | The looting entity must be holding an item |
| `%vanilla_loot_table_name%` | The vanilla loot table name | The loot type must be a container that is generating for a vanilla loot table |
| `%advancement_name%` | The advancement name | The loot type must be an advancement |
| `%explosion_type%` | The type of explosion that caused the loot | The loot generation must have been triggered by an explosion |
| `%item_amount%` | The number of items that were generated | The loot generated must contain items |
| `%experience_amount%` | The amount of experience that was generated | The loot generated must contain the type `experience` |
| `%economy_amount%` | The economy amount that was last generated | The loot generated must contain the type `economy` |
| `%economy_amount_<currency>%` | The economy amount that was last generated, along with the currency that was generated | The loot generated must contain the type `economy` and a currency must be supplied |
| `%economy_amount_<plugin>%` | The economy amount that was last generated for a specific economy plugin | The loot generated must contain the type `economy` |
| `%economy_amount_<plugin>_<currency>%` | The economy amount that was last generated for a specific economy plugin and a specific currency | The loot generated must contain the type `economy` and a currency must be supplied |

### Plugin Compatibility
| Plugin | Placeholder | Description | Requirement |
| --- | --- | --- | --- |
| [RoseStacker](https://www.spigotmc.org/resources/82729/) | `%rosestacker_entity_stack_size%` | The original number of entities in the stack | Must have `trigger-death-event-for-entire-stack-kill` disabled in RoseStacker's config.yml |
|  | `%rosestacker_entity_stack_new_size%` | The remaining number of entities in the stack after some are killed | Same as above |
|  | `%rosestacker_entity_stack_amount_killed%` | The number of entities in the stack that are killed, limited by RoseStacker's loot approximation settings | Same as above |
|  | `%rosestacker_entity_stack_amount_killed_unapproximated%` | The number of entities in the stack that were killed | Same as above |
| [MythicMobs](https://www.spigotmc.org/resources/5702/) | `%mythic_mob_level%` | The level of the Mythic Mob | The `mythicmobs-type` or `mythicmobs-entity` condition must be used first |

## Example
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
            type: item
            item: emerald
            amount:
              min: 3
              max: 5
          1:
            type: command
            value: 'tellraw %player% {"text": "You got %item_amount% emeralds!","color":"yellow"}'
          2:
            type: sound
            sound: 'entity.firework_rocket.twinkle'
            volume: 0.5
```