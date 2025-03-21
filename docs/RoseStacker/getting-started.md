## Introduction
RoseStacker contains an API for looking up and modifying stacks in the world. This API is still in its early stages, if you have any suggestions or find any problems, please create an [issue](https://github.com/Rosewood-Development/RoseStacker/issues/new). 

## Setup
I recommend that you use either Gradle or Maven to include the dependency for RoseStacker in your project. Do not shade the entire plugin into your jar, it should only be added as an implementation. An alternative to using a dependency manager is to download the jar and reference it within your IDE manually.

Replace `$VERSION$` with the version of the plugin you are using. Versions 1.1.0 and newer are available.

### Gradle

```groovy
repositories {
    maven { 
        url = 'https://repo.rosewooddev.io/repository/public/' 
    }
}

dependencies {
    compile 'dev.rosewood:rosestacker:$VERSION$'
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
        <artifactId>rosestacker</artifactId>
        <version>$VERSION$</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

## Getting an API instance
In order to use the API, you must first acquire an API instance. An example plugin class that does this can be found below.

```java
import dev.rosewood.rosestacker.api.RoseStackerAPI;
import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;

public class Example extends JavaPlugin {
    private RoseStackerAPI rsAPI;

    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().isPluginEnabled("RoseStacker")) {
            this.rsAPI = RoseStackerAPI.getInstance();
        }

        // When you want to access the API, check if the instance is null
        if (this.rsAPI != null) {
            // Do stuff with the API here
        }
    }
}
```

## Depend/Softdepend
You will need to add `softdepend: [RoseStacker]` or `depend: [RoseStacker]` to your plugin.yml depending on if your plugin requires RoseStacker to be installed or not.
