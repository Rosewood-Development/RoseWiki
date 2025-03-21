## Introduction
RoseChat contains an API for retreiving plugin data or adding more content, like emojis and channels, with code. If you have any suggestions for the API or find any problems, please create an [issue](https://github.com/Rosewood-Development/RoseChat/issues/new).

## Setup
We recommend that you use either Gradle or Maven to include the dependency for RoseChat in your project. Do not shade the entire plugin into your jar, it should only be added as an implementation. An alternative to using a dependency manager is to download the jar and reference it within your IDE manually.

Replace `$VERSION$` with the version of the plugin you are using. 

### Gradle

```groovy
repositories {
    maven { 
        url = 'https://repo.rosewooddev.io/repository/public/' 
    }
}

dependencies {
    compile 'dev.rosewood:rosechat:$VERSION$'
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
        <artifactId>rosechat</artifactId>
        <version>$VERSION$</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

## Getting an API instance
In order to use the API you must first acquire an API instance. An example plugin class that does this can be found below.

```java
import dev.rosewood.rosechat.api.RoseChatAPI;
import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;

public class Example extends JavaPlugin {
    private RoseChatAPI rcAPI;

    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().isPluginEnabled("RoseChat")) {
            this.rcAPI = RoseChatAPI.getInstance();
        }

        // When you want to access the API, check if the instance is null
        if (this.rcAPI != null) {
            // Do stuff with the API here
        }
    }
}
```

## Depend/Softdepend
You will need to add `softdepend: [RoseChat]` or `depend: [RoseChat]` to your plugin.yml depending on if your plugin requires RoseChat to be installed or not.