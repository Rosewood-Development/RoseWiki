## Introduction
Throughout your use of the API, you will come into contact with several different object types used to manage particles. Below is a list of most of the different types you will come across. 

### PPlayer
Contains information about a Player and the particles and settings that they possess. 
Properties:

* Player UUID
* Saved ParticleGroups
* Owned FixedParticleEffects
* Setting for whether or not particles are hidden
* Flag if the player is moving (not recommended to change)
* Flag if the player is in combat (not recommended to change)

Several methods here are exposed for modifying a player's properties, but it isn't recommended for you to modify any of these, as they will not persist through a player logging out and back in or a server restart. The only way to get values to save is to modify them through use of the API.

### ParticleEffect
This is the wrapper around the Spigot [Particle](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html) enum. You can check if a certain ParticleEffect is enabled through the `ParticleEffect#isEnabled()` method. 

#### ParticleProperty
The following properties exist that a ParticleEffect can have:

* `COLORABLE` - The effect may have color or note color data
* `REQUIRES_MATERIAL_DATA` - The effect requires either item or block data

You can check if a certain ParticleEffect has one of these properties through the `ParticleEffect#hasProperty(ParticleProperty)` method. 

### ParticleStyle
Determines how ParticleEffects will be spawned. These are registered into the plugin on load and custom ones can be added through the API. To access the default styles available in the plugin, use the DefaultStyles class, it has static accessors where you can access the default style objects.

### Particle Data Objects
Some ParticleEffects require data to spawn correctly. The objects that correlate to those data types are below.

#### OrdinaryColor
Determines the color of a particle. Contains red, green, and blue values that range from 0-255. Options for rainbow and random can be accessed through the use of `OrdinaryColor.RAINBOW` and `OrdinaryColor.RANDOM`.

#### NoteColor
Determines the color of the note particle. Contains a note value that ranges from 0-24. Options for rainbow and random can be accessed through the use of `NoteColor.RAINBOW` and `NoteColor.RANDOM`.

#### Material
This is just the Spigot [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) enum. Use [`Material#isBlock()`](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html#isBlock--) to determine if a given material can be used as block data. A material that is not a block can be used as item data. 

### ParticlePair
Contains a player UUID, id, effect, style, and data for a particle. Properties:

* Owner (Player) UUID
* Particle ID
* ParticleEffect
* ParticleStyle
* Material data (item, nullable)
* Material data (block, nullable)
* OrdinaryColor data (nullable)
* NoteColor data (nullable)

If any of the data values are nulled, they will use a default value if the particle effect requires them to spawn.

### PParticle
Contains the spawn location and properties for spawning in a particle. Properties:

* Location of where to spawn the particle
* x, y, and z offsets to randomly offset from the location
* Speed of how fast momentum-enabled particles move
* Directional boolean for if the x, y, and z offsets should modify momentum instead of spread

### ParticleGroup
A PPlayer can own one or more groups. These groups contain a map of IDs to ParticlePairs saved under a String name. 

### FixedParticleEffect
A PPlayer can own one or more fixed particles. Contains a Player UUID to identify the owner, an ID, a Location to spawn at, and a ParticlePair to determine appearance.
These can also be owned by the Console.