## Introduction
RoseLoot contains an API for creating custom loot table conditions. This API is still in its early stages, if you have any suggestions or find any problems, please create an [issue](https://github.com/Rosewood-Development/RoseLoot/issues/new). 

## Setup
I recommend that you use either Gradle or Maven to include the dependency for RoseLoot in your project. Do not shade the entire plugin into your jar, it should only be added as an implementation. An alternative to using a dependency manager is to download the jar and reference it within your IDE manually.

Replace `$VERSION$` with the version of the plugin you are using. Versions 1.1.17 and newer are available.

### Gradle

```groovy
repositories {
    maven { 
        url = 'https://repo.rosewooddev.io/repository/public/' 
    }
}

dependencies {
    compile 'dev.rosewood:roseloot:$VERSION$'
}
```

### Maven

```xml
<repositories>
    <repository>
        <id>rosewood-repo</id>
        <url>https://repo.rosewooddev.io/repository/public/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>dev.rosewood</groupId>
        <artifactId>roseloot</artifactId>
        <version>$VERSION$</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

## Getting an API instance
In order to use the API, you must first acquire an API instance. An example plugin class that does this can be found below.

```java
public class Example extends JavaPlugin {
    private RoseLootAPI rlAPI;

    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().isPluginEnabled("RoseLoot")) {
            this.rlAPI = RoseLootAPI.getInstance();
        }

        // When you want to access the API, check if the instance is null.
        if (this.rlAPI != null) {
            // Do stuff with the API here.
        }
    }
}
```

## Creating Loot Conditions
In order to use the API to create a custom loot table, you need to create a loot condition class. An example class can be found below.

```java
public class WorldCondition extends BaseLootCondition {

    private List<String> worlds;

    public WorldCondition(String tag) {
        super(tag);
    }

    @Override
    protected boolean checkInternal(LootContext context) {
        // Create a condition that checks if the world is matching
        return context.get(LootContextParams.ORIGIN)
                .map(Location::getWorld)
                .map(World::getName)
                .filter(s -> this.worlds.contains(s))
                .isPresent();
    }

    @Override
    public boolean parseValues(String[] values) {
        this.worlds = new ArrayList<>(List.of(values));
        return !this.worlds.isEmpty();
    }

}
```

## Depend/Softdepend
You will need to add `softdepend: [RoseLoot]` or `depend: [RoseLoot]` to your plugin.yml depending on if your plugin requires RoseLoot to be installed or not.