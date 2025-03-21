## Introduction
PlayerPoints contains an API for looking up and modifying a player's points balance.

## Setup
I recommend that you use either Gradle or Maven to include the dependency for PlayerPoints in your project. Do not shade the entire plugin into your jar, it should only be added as an implementation. An alternative to using a dependency manager is to download the jar and reference it within your IDE manually.

Replace `$VERSION$` with the version of the plugin you are using. Versions 3.0.0 and newer are available.

### Gradle

```groovy
repositories {
    maven { 
        url = 'https://repo.rosewooddev.io/repository/public/' 
    }
}

dependencies {
    compile 'org.black_ixx:playerpoints:$VERSION$'
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
        <groupId>org.black_ixx</groupId>
        <artifactId>playerpoints</artifactId>
        <version>$VERSION$</version>
    <scope>provided</scope>
    </dependency>
</dependencies>
```

## Getting an API instance
In order to use the API, you must first acquire an API instance. An example plugin class that does this can be found below.

```java
import org.black_ixx.PlayerPointsAPI;
import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;

public class Example extends JavaPlugin {
    private PlayerPointsAPI ppAPI;

    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().isPluginEnabled("PlayerPoints")) {
            this.ppAPI = PlayerPoints.getInstance().getAPI();
        }

        // When you want to access the API, check if the instance is null
        if (this.ppAPI != null) {
            // Do stuff with the API here
        }
    }
}
```

## Depend/Softdepend
You will need to add `softdepend: [PlayerPoints]` or `depend: [PlayerPoints]` to your plugin.yml depending on if your plugin requires PlayerPoints to be installed or not.