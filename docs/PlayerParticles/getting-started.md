## Introduction
PlayerParticles contains an API for manipulating a player's particles and adding new styles of your own.

## Setup
I recommend that you use either Gradle or Maven to include the dependency for PlayerParticles in your project. Do not shade the entire plugin into your jar, it should only be added as an implementation. An alternative to using a dependency manager is to download the jar and reference it within your IDE manually.

Replace `$VERSION$` with the version of the plugin you are using. Versions 8.0 and newer are available.

### Gradle

```groovy
repositories {
    maven { 
        url = 'https://repo.rosewooddev.io/repository/public/'
    }
}

dependencies {
    implementation 'dev.esophose:playerparticles:$VERSION$'
}
```

### Maven

```xml
<repositories>
    <repository>
        <id>rwd-repo</id>
        <url>https://repo.rosewooddev.io/repository/public/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>dev.esophose</groupId>
        <artifactId>playerparticles</artifactId>
        <version>$VERSION$</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

## Getting an API instance
In order to use the API, you must first acquire an API instance. An example plugin class that does this can be found below.

```java
import dev.esophose.playerparticles.api.PlayerParticlesAPI;
import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;

public class Example extends JavaPlugin {
    private PlayerParticlesAPI ppAPI;

    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().isPluginEnabled("PlayerParticles")) {
            this.ppAPI = PlayerParticlesAPI.getInstance();
        }

        // When you want to access the API, check if the instance is null
        if (this.ppAPI != null) {
            // Do stuff with the API here
        }
    }
}
```

## Depend/Softdepend
You will need to add `softdepend: [PlayerParticles]` or `depend: [PlayerParticles]` to your plugin.yml depending on if your plugin requires PlayerParticles to be installed or not.