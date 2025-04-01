## Particles

PlayerParticles allows you to display particles by specifying three components. These three components are effects, styles, and data. There is a fourth component called the ID which is a unique number to identify a particle. 

## Effects

The effect component is used to determine what the particles will look like. These are the actual Minecraft particle effects that you see throughout the world. 

Not all effects are created equal. Some effects support applying data, such as a color or block/item material. Additionally, some effects can have their momentum influenced by certain styles. This is important for some styles to appear correctly. All this information can be found in the table below.

??? note "Available Effects"

    | Effect Name | Data | Directional | MC Version |
    | --- | --- | --- | --- |
    | ambient_entity_effect | Color | No | 1.7+ |
    | angry_villager | None | No | 1.7+ |
    | ash | None | No | 1.16+ |
    | barrier | None | No | 1.8-1.17 |
    | block | Block Material | No | 1.7+ |
    | block_crumble | Block Material | No | 1.21.2+ |
    | block_marker | Block Material | No | 1.18+ |
    | bubble | None | Yes | 1.7+ |
    | bubble_column_up | None | Yes | 1.13+ |
    | bubble_pop | None | Yes | 1.13+ |
    | campfire_cosy_smoke | None | Yes | 1.14+ |
    | campfire_signal_smoke | None | Yes | 1.14+ |
    | cherry_leaves | None | No | 1.20+ |
    | cloud | None | Yes | 1.7+ |
    | composter | None | No | 1.14+ |
    | crimson_spore | None | No | 1.16+ |
    | crit | None | Yes | 1.7+ |
    | current_down | None | No | 1.13+ |
    | damage_indicator | None | Yes | 1.9+ |
    | dolphin | None | No | 1.13+ |
    | dragon_breath | None | Yes | 1.9+ |
    | dripping_dripstone_lava | None | No | 1.17+ |
    | dripping_dripstone_water | None | No | 1.17+ |
    | dripping_honey | None | No | 1.15+ |
    | dripping_lava | None | No | 1.7+ |
    | dripping_obsidian_tear | None | No | 1.16+ |
    | dripping_water | None | No | 1.7+ |
    | dust | Color | No | 1.7+ |
    | dust_color_transition | Color Transition | No | 1.17+ |
    | dust_pillar | Block Material | No | 1.20.5+ |
    | dust_plume | None | Yes | 1.20.5+ |
    | egg_crack | None | No | 1.20.5+ |
    | elder_guardian | None | No | 1.8+ (disabled by default) |
    | electric_spark | None | Yes | 1.17+ |
    | enchant | None | Yes | 1.7+ |
    | enchanted_hit | None | Yes | 1.7+ |
    | end_rod | None | Yes | 1.9+ |
    | entity_effect | Color | No | 1.7+ |
    | explosion | None | No | 1.7+ |
    | explosion_emitter | None | No | 1.7+ |
    | falling_dripstone_lava | None | No | 1.17+ |
    | falling_dripstone_water | None | No | 1.17+ |
    | falling_dust | Block Material | No | 1.10+ |
    | falling_honey | None | No | 1.15+ |
    | falling_lava | None | No | 1.7+ |
    | falling_nectar | None | No | 1.15+ |
    | falling_obsidian_tear | None | No | 1.16+ |
    | falling_spore_blossom | None | No | 1.17+ |
    | falling_water | None | No | 1.7+ |
    | firefly | None | No | 1.21.5+ |
    | firework | None | Yes | 1.7+ |
    | fishing | None | Yes | 1.7+ |
    | flame | None | Yes | 1.7+ |
    | flash | None | No | 1.14+ (disabled by default) |
    | footstep | None | No | 1.7-1.12 |
    | glow | None | No | 1.17+ |
    | glow_squid_ink | None | Yes | 1.17+ |
    | gust | None | No | 1.20.5+ |
    | gust_emitter_large | None | No | 1.20.5+ |
    | gust_emitter_small | None | No | 1.20.5+ |
    | happy_villager | None | No | 1.7+ |
    | heart | None | No | 1.7+ |
    | infested | None | No | 1.20.5+ |
    | instant_effect | None | No | 1.7+ |
    | item | Item Material | No | 1.7+ |
    | item_cobweb | None | No | 1.20.5+ |
    | item_slime | None | No | 1.7+ |
    | item_snowball | None | No | 1.7+ |
    | landing_honey | None | No | 1.15+ |
    | landing_lava | None | No | 1.7+ |
    | landing_obsidian_tear | None | No | 1.16+ |
    | large_smoke | None | Yes | 1.7+ |
    | lava | None | No | 1.7+ |
    | light | None | No | 1.17 only |
    | mycelium | None | No | 1.7+ |
    | nautilus | None | Yes | 1.13+ |
    | note | Note Color | No | 1.9+ |
    | ominous_spawning | None | Yes | 1.20.5+ |
    | pale_oak_leaves | None | No | 1.21.4+ |
    | poof | None | Yes | 1.7+ |
    | portal | None | Yes | 1.9+ |
    | raid_omen | None | No | 1.20.5+ |
    | rain | None | No | 1.7+ |
    | reverse_portal | None | Yes | 1.16+ |
    | scrape | None | Yes | 1.17+ |
    | sculk_charge | None | Yes | 1.19+ |
    | sculk_charge_pop | None | Yes | 1.19+ |
    | sculk_soul | None | Yes | 1.19+ |
    | shriek | None | No | 1.19+ |
    | small_flame | None | Yes | 1.17+ |
    | small_gust | None | No | 1.20.5+ |
    | smoke | None | Yes | 1.7+ |
    | sneeze | None | Yes | 1.14+ |
    | snowflake | None | Yes | 1.17+ |
    | sonic_boom | None | No | 1.19+ |
    | soul | None | Yes | 1.16+ |
    | soul_fire_flame | None | Yes | 1.16+ |
    | spell | None | No | 1.7+ |
    | spit | None | Yes | 1.11+ |
    | splash | None | No | 1.7+ |
    | spore_blossom_air | None | No | 1.17+ |
    | squid_ink | None | Yes | 1.13+ |
    | sweep_attack | None | No | 1.9+ |
    | tinted_leaves | Color | No | 1.21.5+ |
    | totem_of_undying | None | Yes | 1.11+ |
    | trail | Color | No | 1.21.2+ |
    | trial_omen | None | No | 1.20.5+ |
    | trial_spawner_detection | None | Yes | 1.20.5+ |
    | trial_spawner_detection_ominous | None | Yes | 1.20.5+ |
    | underwater | None | No | 1.7+ |
    | vibration | Vibration | No | 1.17+ (disabled by default) |
    | warped_spore | None | No | 1.16+ |
    | wax_off | None | Yes | 1.17+ |
    | wax_on | None | Yes | 1.17+ |
    | white_ash | None | No | 1.16+ |
    | witch | None | No | 1.7+ |

</details>

## Styles

The style component is used to determine what shape the particles will spawn in. Some styles may spawn particles with momentum applied to them. If an effect is used that is not directional, these styles may not look correct. Styles that are marked as event-based mean that they spawn based on some sort of in-game event, you should be able to guess what the events are. Lastly, most styles are able to be used in fixed effects, but not all can be due to restraints. 

??? note "Available Styles"

    | Style Name | Event-Based | Fixable | Momentum |
    | --- | --- | --- | --- |
    | arrows | Yes | No | No |
    | batman | No | Yes | No |
    | beam | No | Yes | No |
    | blockbreak | Yes | No | Yes |
    | blockplace | Yes | No | Yes |
    | celebration | No | Yes | No |
    | chains | No | Yes | No |
    | companion | No | Yes | No |
    | cube | No | Yes | No |
    | death | Yes | No | No |
    | feet | No | Yes | No |
    | halo | No | Yes | No |
    | hurt | Yes | No | No |
    | invocation | No | Yes | Yes |
    | move | Yes | No | No |
    | normal | No | Yes | No |
    | orbit | No | Yes | No |
    | overhead | No | Yes | No |
    | point | No | Yes | No |
    | popper | No | Yes | No |
    | pulse | No | Yes | Yes |
    | quadhelix | No | Yes | No |
    | rings | No | Yes | No |
    | sphere | No | Yes | No |
    | spin | No | Yes | No |
    | spiral | No | Yes | No |
    | swords | Yes | No | No |
    | teleport | Yes | No | Sometimes |
    | thick | No | Yes | No |
    | twins | No | Yes | No |
    | vortex | No | Yes | No |
    | whirl | No | Yes | Yes |
    | whirlwind | No | Yes | Yes |
    | wings | No | No | No |

## Data

The final component of data is used to modify the appearance of the effects. Not all effects are able to accept data, so this component can be omitted in this case. There are four types of data: color, note color, block material, and item material. Information about each of these can be found below.

#### Color Data

As the name implies, this data type changes the color of the effect. There are three different formats that can be used: rgb, hex, and color name. Below are each of the formats with an example to make the color light blue. 

##### RGB

Consists of red, green, and blue values.

Format: `r g b`
Example: `173 216 230`

##### Hex Code

Consists of red, green, and blue values in hexadecimal notation.

Format: `#xxxxxx`
Example: `#add8e6`

##### Color Name

Consists of a defined color name.

Format: `color_name`
Example: `light_blue`

??? note "Available Colors"

    | Color Name | RGB Value | Hex Value |
    | --- | --- | --- |
    | red | 255 0 0 | #ff0000 |
    | orange | 255 140 0 | #ff8c00 |
    | yellow | 255 255 0 | #ffff00 |
    | lime | 50 205 50 | #32cd32 |
    | green | 0 128 0 | #008000 |
    | blue | 0 0 255 | #0000ff |
    | cyan | 0 139 139 | #008b8b |
    | light_blue | 173 216 230 | #add8e6 |
    | purple | 138 43 226 | #8a2be2 |
    | magenta | 202 31 123 | #ca1f7b |
    | pink | 255 182 193 | #ffb6c1 |
    | brown | 139 69 19 | #8b4513 |
    | black | 0 0 0 | #000000 |
    | gray | 128 128 128 | #808080 |
    | light_gray | 192 192 192 | #c0c0c0 |
    | white | 255 255 255 | #ffffff |
    | rainbow | N/A | N/A |
    | random | N/A | N/A |

#### Note Color Data

The note color is defined by a single number between 0 and 24. Each number represents a different color, some being only slightly different. A table of what colors each number are can be found below.

Note: In versions of Minecraft lower than 1.14, the note color calculations were broken which made about half the colors appear as gray. 

??? note "Available Note Colors"

    | Note # | Approximate Color |
    | --- | --- |
    | 0 | lime |
    | 1 | lime |
    | 2 | yellow |
    | 3 | orange |
    | 4 | orange |
    | 5 | red |
    | 6 | red |
    | 7 | red |
    | 8 | magenta |
    | 9 | magenta |
    | 10 | purple |
    | 11 | purple |
    | 12 | purple |
    | 13 | blue |
    | 14 | blue |
    | 15 | blue |
    | 16 | blue |
    | 17 | cyan |
    | 18 | cyan |
    | 19 | lime |
    | 20 | lime |
    | 21 | lime |
    | 22 | lime |
    | 23 | lime |
    | 24 | lime |
    | rainbow | N/A |
    | random | N/A |

#### Item/Block Material Data

Item/Block material data is the material name of either an item or a block, depending on which type is required. An example of a block would be `diamond_block` and an item example would be `golden_apple`.

#### Color Transition Data

This data is identical to Color Data, except you provide two colors instead of just one.

#### Vibration Data

A single number 1 or higher which represents the duration of the vibration.