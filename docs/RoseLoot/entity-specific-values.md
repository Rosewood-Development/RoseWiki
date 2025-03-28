## Introduction
You can check for conditions that are specific to certain entities.  These conditions are used in the same way as other conditions, and you can visit the [Generic Values](generic-values.md) page to learn more about them.

## Entity-Specific Values

| Entity Type | Condition | Description | Values | Example |
| --- | --- | --- | --- | --- |
| **Allay** |  |  |  |  |
| **Axolotl** | `axolotl-playing-dead` | Axolotl must be playing dead | None | `axolotl-playing-dead` |
|  | `axolotl-variant` | Axolotl must be a specific variant | [Axolotl Variant](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Axolotl.Variant.html), requires 1 or more | `axolotl-variant:blue` |
| **Bat** | `bat-sleeping` | Bat must be asleep hanging on a block | None | `bat-sleeping` |
| **Bee** | `bee-angry` | Bee must be angry and trying to sting you | None | `bee-angry` |
|  | `bee-has-hive` | Bee must have a hive it calls home | None | `bee-has-hive` |
|  | `bee-has-stung` | Bee must be suffering the loss of its stinger | None | `bee-has-stung` |
|  | `bee-has-flower` | Bee must be *bee*-lining towards a flower or actively pollinating it | None | `bee-has-flower` |
|  | `bee-has-nectar` | Bee must be happily covered in pollen | None | `bee-has-nectar` |
| **Bogged** | `bogged-sheared` | Bogged must be sheared | None | `bogged-sheared` |
| **Blaze** |  |  |  |  |
| **Breeze** | | | | |
| **Camel** | `camel-dashing` | Camel must be dashing | None | `camel-dashing` |
| **Cat** | `cat-type` | Cat must be a certain type | [Cat Type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Cat.Type.html), requires 1 or more | `cat-type:siamese` |
|  | `cat-collar-color` | Cat must have a certain color of collar | [Dye Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/DyeColor.html), requires 1 or more | `cat-collar-color:pink` |
| **Cave Spider** |  |  |  |  |
| **Chicken** | `chicken-variant` | Chicken must be of a certain variant | [Chicken Variant](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Chicken.Variant.html), requires 1 or more | `chicken-variant:temperate` |
| **Cod** |  |  |  |  |
| **Cow** | `cow-variant` | Cow must be of a certain variant | [Cow Variant](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Cow.Variant.html), requires 1 or more | `cow-variant:cold` |
| **Creeper** | `creeper-charged` | Creeper must have been struck by lightning and charged up | None | `creeper-charged` |
| **Dolphin** |  |  |  |  |
| **Donkey** |  |  |  |  |
| **Drowned** |  |  |  |  |
| **Elder Guardian** |  |  |  |  |
| **Ender Dragon** | `ender-dragon-phase` | Ender Dragon must be in a specific fight phase | [Ender Dragon Phase](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EnderDragon.Phase.html), requires 1 or more | `ender-dragon-phase:land_on_portal` |
| **Enderman** | `enderman-holding-block` | Enderman must be holding a block or a specific block | [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html), requires 0 or more. If 0, matches against any material. | `enderman-holding-block:grass_block` |
| **Endermite** |  |  |  |  |
| **Evoker** |  |  |  |  |
| **Fox** | `fox-type` | Fox must be of a certain type | [Fox Type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Fox.Type.html), requires 1 or more | `fox-type:snow` |
|  | `fox-crouching` | Fox must be crouching and getting ready to pounce | None | `fox-crouching` |
| **Frog** | `frog-variant` | Frog must be of a certain variant | [Frog Variant](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Frog.Variant.html), requires 1 or more | `frog-variant:temperate` |
| **Ghast** |  |  |  |  |
| **Giant** |  |  |  |  |
| **Glow Squid** | `glow-squid-dark` | Bravo Six going dark, glow squid must be fleeing an attacker | None | `glow-squid-dark` |
| **Goat** | `goat-screaming` | Goat must be of the angrily screaming variety | None | `goat-screaming` |
|  | `goat-has-left-horn` | Goat must still have its left horn | None | `goat-has-left-horn` |
|  | `goat-has-right-horn` | Goat must still have its right horn | None | `goat-has-right-horn` |
| **Guardian** |  |  |  |  |
| **Hoglin** | `hoglin-unhuntable` | Hoglin must be unable to be hunted by piglins | None | `hoglin-unhuntable` |
| **Horse** | `horse-armored` | Horse must have a specific kind of armor | `diamond`, `gold`, `iron`, or `leather`. If no value is provided, will be true if any armor is equipped. | `horse-armored:diamond` |
|  | `horse-style` | Horse must be of a specific style | [Horse Style](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Horse.Style.html), requires 1 or more | `horse-style:whitefield` |
|  | `horse-color` | Horse must be of a specific color | [Horse Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Horse.Color.html), requires 1 or more | `horse-color:chestnut` |
| **Husk** | `husk-converting` | Husk must be converting to a zombie | None | `husk-converting` |
| **Illusioner** | `illusioner-spell` | Illusioner must be casting a specific spell | [Spellcaster Spell](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Spellcaster.Spell.html), requires 1 or more | `illusioner-spell:wololo` |
| **Iron Golem** | `iron-golem-player-created` | Iron Golem must have been created by a player | None | `iron-golem-player-created` |
| **Llama** | `llama-decor` | Llama must have a specific decor equipped | [Carpet Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html), requires 1 or more | `llama-decor:red_carpet` |
|  | `llama-color` | Llama must be a specific color | [Llama Color](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Llama.Color.html), requires 1 or more | `llama-color:creamy` |
| **Magma Cube** | `magma-cube-size` | Magma Cube must be a specific size | Positive Number, requires 1 or more | `magma-cube-size:3` |
| **Mule** |  |  |  |  |
| **Mooshroom** | `mooshroom-variant` | Mooshroom must be of a specific variant | [Mooshroom Variant](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/MushroomCow.Variant.html), requires 1 or more | `mooshroom-variant:brown` |
| **Ocelot** |  |  |  |  |
| **Panda** | `panda-main-gene` | Panda must have a specific main gene | [Panda Gene](https://helpch.at/docs/1.16.1/org/bukkit/entity/Panda.Gene.html), requires 1 or more | `panda-main-gene:weak` |
|  | `panda-hidden-gene` | Panda must have a specific hidden gene | [Panda Gene](https://helpch.at/docs/1.16.1/org/bukkit/entity/Panda.Gene.html), requires 1 or more | `panda-hidden-gene:playful` |
| **Parrot** | `parrot-variant` | Parrot must be a specific variant | [Parrot Variant](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Parrot.Variant.html) | `parrot-variant:blue` |
| **Phantom** | `phantom-size` | Phantom must be a specific size | Positive Number, requires 1 or more | `phantom-size:2` |
| **Pig** | `pig-variant` | Pig must be of a certain variant | [Pig Variant](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Pig.Variant.html), requires 1 or more | `pig-variant:warm` |
| **Piglin Brute** | `piglin-brute-converting` | Piglin Brute must be converting to a zombified piglin | None | `piglin-brute-converting` |
|  | `piglin-brute-immune-to-zombification` | Piglin Brute must be unable to turn into a zombified piglin | None | `piglin-brute-immune-to-zombification` |
| **Piglin** | `piglin-converting` | Piglin must be converting to a zombified piglin | None | `piglin-converting` |
|  | `piglin-immune-to-zombification` | Piglin must be unable to turn into a zombified piglin | None | `piglin-immune-to-zombification` |
|  | `piglin-unable-to-hunt` | Piglin must be unable to hunt for hoglins | None | `piglin-unable-to-hunt` |
| **Pillager** |  |  |  |  |
| **Polar Bear** |  |  |  |  |
| **Pufferfish** | `pufferfish-puff-state` | Pufferfish must be inflated to a certain amount | Whole number between 0 and 2, 0 being uninflated and 2 being fully inflated. Requires 1 or more. | `pufferfish-puff-state:2` |
| **Rabbit** | `rabbit-type` | Rabbit must be a specific type | [Rabbit Type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Rabbit.Type.html), requires 1 or more | `rabbit-type:the_killer_bunny` |
| **Ravager** |  |  |  |  |
| **Salmon** |  |  |  |  |
| **Sheep** | `sheep-sheared` | Sheep must be sheared | None | `sheep-sheared` |
|  | `sheep-color` | Sheep must be a specific color | [Dye Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/DyeColor.html), requires 1 or more | `sheep-color:pink` |
| **Shulker** |  |  |  |  |
| **Silverfish** |  |  |  |  |
| **Skeleton** | `skeleton-converting` | Skeleton must be freezing and converting to a stray | None | `skeleton-converting` |
| **Skeleton Horse** |  |  |  |  |
| **Slime** | `slime-size` | Slime must be a specific size | Positive Number, requires 1 or more | `slime-size:3` |
| **Sniffer** | `sniffer-state` | Sniffer must be in a certain state | [Sniffer State](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Sniffer.State.html), requires 1 or more | `sniffer-state:feeling_happy` |
| **Snowman** | `snowman-no-pumpkin` | Snowman must not have its pumpkin | None | `snowman-no-pumpkin` |
| **Spider** |  |  |  |  |
| **Squid** |  |  |  |  |
| **Stray** |  |  |  |  |
| **Strider** | `strider-shivering` | Strider must be outside of lava and shivering | None | `strider-shivering` |
| **Tadpole** |  |  |  |  |
| **Trader Llama** | `trader-llama-decor` | Trader Llama must have a specific decor equipped | [Carpet Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html), requires 1 or more | `llama-decor:red_carpet` |
|  | `llama-color` | Trader Llama must be a specific color | [Llama Color](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Llama.Color.html), requires 1 or more | `llama-color:creamy` |
| **Tropical Fish** | `tropical-fish-body-color` | Tropical Fish must have a specific body color | [Dye Color](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html), requires 1 or more | `tropical-fish-body-color:red` |
|  | `tropical-fish-pattern` | Tropical Fish must have a specific pattern | [Tropical Fish Pattern](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/TropicalFish.Pattern.html), requires 1 or more | `tropical-fish-pattern:sunstreak` |
|  | `tropical-fish-pattern-color` | Tropical Fish must have a specific pattern color | [Dye Color](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html), requires 1 or more | `tropical-fish-pattern-color:blue` |
| **Turtle** |  |  |  |  |
| **Vex** | `vex-charging` | Vex must be charging towards its target | None | `vex-charging` |
| **Villager** | `villager-profession` | Villager must have a specific profession | [Villager Profession](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Villager.Profession.html), requires 1 or more | `villager-profession:librarian` |
|  | `villager-type` | Villager must be a specific type | [Villager Type](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Villager.Type.html), requires 1 or more | `villager-type:snow` |
|  | `villager-level` | Villager must have a level greater than or equal to the given value | Positive Number, requires 1 or more | `villager-level:3` |
| **Vindicator** |  |  |  |  |
| **Wandering Trader** |  |  |  |  |
| **Warden** |  |  |  |  |
| **Witch** |  |  |  |  |
| **Wither** |  |  |  |  |
| **Wither Skeleton** |  |  |  |  |
| **Wolf** | `wolf-angry` | Wolf must be angry and attacking a target | None | `wolf-angry` |
|  | `wolf-color` | Wolf must have a specific collar color | [Dye Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/DyeColor.html), requires 1 or more | `wolf-color:magenta` |
| | `wolf-variant` | Wolf must be a certain variant | [Wolf Variant](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Wolf.Variant.html), requires 1 or more | `wolf-variant:spotted` |
| **Zoglin** |  |  |  |  |
| **Zombie** | `zombie-converting` | Zombie must be converting to a drowned | None | `zombie-converting` |
| **Zombie Horse** |  |  |  |  |
| **Zombie Villager** | `zombie-villager-converting` | Zombie Villager must be getting cured | None | `zombie-villager-converting` |
|  | `zombie-villager-profession` | Zombie Villager must have a specific profession | [Villager Profession](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Villager.Profession.html), requires 1 or more | `zombie-villager-profession:cleric` |
| **Zombified Piglin** | `zombified-piglin-angry` | Zombified Piglin must be angry at a player | None | `zombified-piglin-angry` |