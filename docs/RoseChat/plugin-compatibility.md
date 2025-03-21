## Introduction
RoseChat offers support for various plugins to allow you to have the best experience while using it. If you want us to add more plugin compatibility, join our Discord (linked in the footer) and suggest it to us!

## Server Compatibility
RoseChat is compatible with Spigot and any forks. We recommend using [Paper](https://papermc.io/) to run your server.  CraftBukkit servers will not be compatible with the plugin.

We support Minecraft versions **1.16.5** and newer running **Java 17**.

If you wish to use this plugin on a 1.16.5 server (newer versions do not need this), you will need to use [Paper](https://papermc.io/) (or a fork of Paper), Java 17, and add the flag `-DPaper.IgnoreJavaVersion=true` to your server's startup parameters.

## Plugin Compatibility
RoseChat has compatibility added with the following plugins:

* Vault
    * Allows checking offline players' permissions and using the %vault_rank% placeholder without PlaceholderAPI.
* PlaceholderAPI
    * Allows placeholders to be used within chat formats, chat messages, and locale messages. Also adds [custom placeholders](https://github.com/Rosewood-Development/RoseChat/wiki/PlaceholderAPI-Support) to be used in other plugins.
* DiscordSRV
    * Allows messages sent from RoseChat to be displayed to and from Discord servers, with full formatting support for both Discord and RoseChat.
* ProtocolLib
    * Allows messages to be deleted.
* WorldGuard
    * Allows channels to only be accessible in a region.
* Towny
    * Allows channels for towns, nations and allies.
* SuperiorSkyblock
    * Allows channels for island members, local players, and coop members.
* SimpleClans
    * Allows channels for clan members and allies.
* mcMMO
    * Allows channels for parties.
* MarriageMaster
    * Allows channels for partners.
* KingdomsX
    * Allows channels for nation members, kingdom members, allies, truce players and enemies.
* ~~IridiumSkyblock~~
    * ~~Allows channels for island members, local players, and trusted members.~~
    * This has been temporarily removed as the majority of users are using IridiumSkyblock 4.0, which does not have an API.
* FactionsUUID
    * Allows channels for faction members, allies, mods, and truce players.
* FabledSkyblock
    * Allows channels for island members and local players.
* BentoBox
    * Allows channels for island members, local players, and coop members.
* HuskTowns
    * Allows channels for town members.

## Other Compatibility
Our plugins are compatible with languages other than English, because they are completely translatable! Every message within the plugin is included in a language file and can be edited.