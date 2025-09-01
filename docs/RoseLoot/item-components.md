## Introduction
Item components allow you to modify the items spawned by RoseLoot in ways that Item Meta can't.  RoseLoot supports item components since 1.21.3 and only on Paper servers.

## Adding Components
RoseLoot supports the majority of components that are in Minecraft (70+ of them!), notably missing `custom_data`, you will have to use the NBTAPI plugin for that one, more details [here](item-meta.md#nbt-data).  Due to some components changing between Minecraft versions (even minor versions), your loot tables may break without warning when upgrading your server when using these features.

In general, component loot table entries follow a similar format to how you would write Minecraft item components, except replace underscores (`_`) in property names with hyphens (`-`) and use YAML syntax instead of SNBT/Json.  Each component is added by name under the `components` section of an item.

Here's a basic example to make an edible emerald using the `consumable`, `food`, and `item-name` components.  You can view the component formats on the Minecraft Wiki for comparison: [consumable](https://minecraft.wiki/w/Data_component_format/consumable), [food](https://minecraft.wiki/w/Data_component_format/food), [item-name](https://minecraft.wiki/w/Data_component_format/item_name).
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
            components:
              item-name: 'Edible Emerald'
              consumable:
                consume-seconds: 2
                animation: eat
                sound: 'entity.generic.eat'
                has-consume-particles: true
                probability: 1.0
                on-consume-effects:
                  0:
                    type: teleport_randomly
                    diameter: 4.0
                  1:
                    type: apply_effects
                    effects:
                      0:
                        id: nausea
                        amplifier: 0
                        duration: 120
                        ambient: false
                        show-particles: true
                        show-icon: true
              food:
                nutrition: 1
                saturation: 2
                can-always-eat: true
```
