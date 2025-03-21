RoseChat can be tricky to set up at times, so this short guide will explain how you can format your chat.

The most important files are the [channels.yml](configuration-files.md#channelsyml) and [custom-placeholders.yml](configuration-files.md#custom-placeholdersyml) files.

The channels.yml file defines the different channels that players can chat in. You can edit, remove, and add your own channels to this file.<br>
The `formats` section defines the formats of the channel. Different channels can have different formats.<br>

The default `global` channel has this format: `{prefix}{player}{separator}{message}`.<br>
This format would show up in chat like `[Staff] Lilac » Your chat message`.<br>
Each word surrounded by brackets is a **custom placeholder**. You can edit these placeholders in the `custom-placeholders.yml` file.<br>

The default `player` placeholder looks like this:
```yaml
player:
  text:
    default: "%player_nickname%"
  hover:
    default:
      - "&7Username: &f%player_name%"
      - "&7Click to Message"
  click:
    action: SUGGEST_COMMAND
    default: "/msg %player_name% "
```
It is split into 3 parts. The `text` section is the text that is displayed in chat. The `hover` section is the text that is displayed when a player hovers over the text in chat. The `click` section is what happens when a player clicks the text in chat.<br>
These sections can be edited, removed, or added if they do not exist.<br>
They can also contain placeholders to further customise your chat.

The default `prefix` placeholder looks like this:
```yaml
prefix:
  text:
    condition: "%vault_rank%"
    default: "&7"
    mod: "&8[&dMod&8] &d"
    admin: "&8[#C0FFEEAdmin&8] #C0FFEE"
  hover:
    condition: "%vault_rank%"
    mod:
      - "&dThis player moderates the server!"
    admin:
      - "&cThis player administrates the server!"
```
This is slightly more complicated than the `player` section, but it should be easy to understand after an explanation.<br>
In this section, a `condition` is used.<br>
This condition checks the placeholder `%vault_rank%`, which returns the name of the player's rank. For example, `mod` or `admin`.<br>
The options underneath the condition are the results of condition. As `%vault_rank%` returns a rank, these sections are the ranks. You can edit this to add or remove ranks.<br>
If a player's vault rank is `mod` then their prefix will be `&8[&dMod&8] &d`.<br>

More information about conditions can be found [here](configuration-files.md#custom-placeholdersyml).

### Example ###
An example set of basic placeholders can be found below. These don't use conditions and are simple to set up.<br>
```yaml
prefix:
  text:
    # Uses the %luckperms_prefix% placeholder to get a player's prefix.
    default: "%luckperms_prefix%"

player:
  text:
    # Gets the player's nickname.
    default: "%player_nickname%"
  hover:
    # Displays this message when someone hovers over the player's nickname.
    default:
      - "&7Username: &f%player_name%"
      - "&7Click to Message"
  click:
    # Suggests a command when someone clicks on the player's nickname.
    action: SUGGEST_COMMAND
    default: "/msg %player_name% "
```