## Introduction
Resource Packs can heavily change the way your server looks, and with RoseChat these can be used in chat too.

### Making a Resource Pack
If you are unsure how to create a resource pack, there are plenty of tutorials online.
This is a text-based tutorial from the [Minecraft Wiki](https://minecraft.wiki/w/Tutorials/Creating_a_resource_pack); if you prefer video tutorials, you can use YouTube tutorials to get started.

### Custom Icons & Emojis
Once you have a resource pack created, you should create another folder in the `assets` folder. This is to keep your files more organized; content for RoseChat will go in this folder.

![Two folders in the assets directory](https://user-images.githubusercontent.com/46502463/158429596-fc6727ea-c27c-4a25-a2b0-7f04e5d6ead2.png)

After this, a folder called `textures` is needed inside it.

![The textures folder in the rosechat directory](https://user-images.githubusercontent.com/46502463/158429503-96e87541-24ea-451a-ac73-2c55f9a2fcfc.png)

Your emojis/icons should go in this folder.
Note: The maximum size for these is 256x256.

![Emojis in the textures folder.](https://user-images.githubusercontent.com/46502463/158429435-7dfade13-406d-405d-b5cc-ca1616388a54.png)

Then, navigate back to your `assets` folder. Enter the `minecraft` folder, or create it if it does not exist. 
Enter the `font` folder, or create it if it does not exist.

A file called `default.json` needs to be created, the name of this file will be the name of the font. This is also the name used for the font in RoseChat's `replacements.yml`. I recommend sticking to `default.json` as it is the most convenient.

![The default.json file in the font folder](https://user-images.githubusercontent.com/46502463/200878963-7dd6a5eb-ebf5-492d-bd36-a30c59971fdb.png)

As this is a json file, it may be easier to use a Json Validator such as [JSONLint](https://jsonlint.com/) to make sure your file is formatted correctly.

At first, you should copy this into the file. This tells Minecraft what will be providing the font.<br>
This example displays multiple emojis so you can see how multiple are created.
```json
{
  "providers": [
    {
      "type": "bitmap",
      "file": "emoji:rosewood.png",
      "ascent": 8,
      "height": 8,
      "chars": [
        "\uE000"
      ]
    },
    {
      "type": "bitmap",
      "file": "emoji:smile.png",
      "ascent": 8,
      "height": 8,
      "chars": [
        "\uE001"
      ]
    }
  ]
}
```
The `type` tells Minecraft that the font uses bitmap images. This means you can use one image per character.

The `file` tells Minecraft which file to use. You should use the name of the folder you created instead of "rosechat", and your image file instead of "rosewood.png", the file extension is needed.

The `ascent` is how high up from the line the symbol should be. This cannot be bigger than the height.

The `height` is the size of the image.

The `chars` are the unicode numbers of the character to use. Every instance of these characters, using this font, will be replaced.

When using this in RoseChat, defining the font is easy and won't cause any issues. However, if you intend to use the resource pack elsewhere, or decide to edit the "default" font, you should be careful of which characters you use. This is because players who speak different languages may have some of their characters changed. We recommend using characters from the [Private Use Area](https://www.fileformat.info/info/unicode/block/private_use_area/index.htm) section of unicode. These are characters from \uE000 to \uF8FF, specifically reserved to be used like this.

In replacements.yml, you can optionally provide a `font` option if the font differs from `default`. For example:

```yaml
rosewood:
  input:
    text: ':rosewood:'
  output:
    replacement: "\uE000"
    hover: '&b&o:rosewood:'
```
This tells RoseChat to replace all instances of `:rosewood:` with the \uE000 character and the `emoji` font. This character will have been changed by the resource pack and therefore should show the image in-game, like this:

![The result](https://user-images.githubusercontent.com/46502463/158437722-a13ac2d0-48ed-42ab-9a6c-298a228be4b8.png)

#### Using Emojis as Prefixes
To use a replacement as a prefix, you must follow the steps above and create a new replacement in `replacements.yml`. Once this is done, you can use [custom-placeholders.yml](configuration-files.md#custom-placeholdersyml) to tell the plugin where the emoji should be seen. For example:

```yaml
prefix:
  text:
    default: ":admin-prefix:"
```
After adding `{prefix}` to a format, this will display the emoji wherever you decide.

![An admin prefix](https://user-images.githubusercontent.com/46502463/158439477-535887a3-f6c7-4b70-98c4-d505f6ba8f5e.png)

#### Compatibility with other plugins (ItemsAdder, Oraxen, etc.)
While using these plugins, RoseChat emojis may not work as these plugins create the resource pack and overwrite the characters.
It is recommended to use the other plugin for these emojis and prefixes as they can be used in multiple places and is easier to set up.
However, if you want to keep using RoseChat emojis, the simplest way is to change the replacement and `chars` unicode character. For example, if the character is `\uE000`, changing it to `\uE100` should resolve the issue (if you have more emojis/guis in the other plugin, you may need to increase the number to something higher).

### Shaders
This, is an example of a shader:

![Fancy Shader](https://user-images.githubusercontent.com/46502463/158444719-18a9d46e-259e-427a-9426-3a5d8ef3c0aa.gif)

#### In RoseChat
In RoseChat, shaders will work the same as below, by displaying them using a tag. 
However, this creates some issues. As the shader replaces a color, such as `#FFFFFE`, players will not be able to use this color in-game or their message will be using the shader.
To resolve this, RoseChat has a config option called `core-shader-colors`. This is a list of colors that RoseChat will shift slightly (for example, changing `#FFFFFE` to `#FFFFFD`) to allow players to use the color without using the shader. This change is not visible as the two colors are practically invisible.

#### Custom Shaders
Custom shaders are a _very_ complex topic, which requires knowledge of GLSL shaders. 
There's not much information related to text shaders, but [this guide](https://github.com/Vekhove/Minecraft-Text-Shaders/wiki) may help you create them.

Once you have shaders, displaying them in chat is simple.
You will need to create a custom replacement(configuration-files.md#replacementsyml), similar to this:
```yaml
bounce:
  prefix: '<bounce>'
  suffix: '</bounce>'
  format: '{bounce}'
```
As this uses a format, a [custom placeholder](configuration-files.md#custom-placeholdersyml) is also needed, similar to this:
```yaml
bounce:
  text:
    default: "#FFFFFC%tagged%"
```
Simply replace the word 'bounce' with the name of your effect, and replace the hex color with the color needed to use your effect.
Now, shaders should work in your chat! Players will need the [permission](commands-&-permissions.md) `rosechat.tag.bounce` and `rosechat.tags.<location>` to use it.<br/>
![Bouncing Text](https://user-images.githubusercontent.com/46502463/158844174-5416ac64-f108-4e88-8f1d-538a2699bdd5.gif)