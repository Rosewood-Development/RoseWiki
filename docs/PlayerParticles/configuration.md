## Introduction

Once the plugin has been run on your server at least once, a PlayerParticles folder will appear in your plugins folder. This folder will contain the following files and folders:

* effects/
* locale/
* styles/
* config.yml
* playerparticles.db
* preset_groups.yml

In versions of PlayerParticles v7.0 or newer, all configuration files will automatically update to include the latest settings when updating to a newer plugin version. Details about each of these files/folders can be found in their respective sections below.

### config.yml

This is where the bulk of the configuration for the plugin exists. Each of the settings contains a description of what the setting does, along with what its default value is. It is recommended that you read through all the configuration to ensure that you get the experience that you are expecting. In general, if you aren't sure about what a setting does, make sure that you fully read the description. 

There are two sub-sections within the config.yml file: mysql-settings, and gui-icon. The mysql-settings section is for deciding if you want to use SQLite or MySQL for the plugin's data storage. SQLite will be the fastest option, but MySQL will allow you to carry across player settings across multiple servers in the case that you use BungeeCord or similar. The gui-icon section is to decide which icons will be displayed in the GUI for each of the buttons. The default icons should be good enough but if you want to change them then option is there. 

### preset_groups.yml

Information about preset groups can be found in the comments at the top of the preset_groups.yml file located in the plugins/PlayerParticles folder.

### Effect/Style Settings

New to PlayerParticles v7.0, you can now configure individual settings for effects and styles. Don't want certain effects or styles to be available across the whole plugin? They can be disabled with ease. In addition to this, if you want to change the name of an effect or style, that option is also available. If you do decide to change any of the names, make sure they don't contain any spaces. 

The effect settings only contain the name and if it should be enabled. Style settings on the other hand include a bunch of different settings to customize the appearance of the styles to your liking. 

### Locale

You can choose which language to use for the plugin. The language files provided by default can be found in the /locale/ folder, and the setting to choose which you'd like to use is located in the config.yml named 'locale'. By default, en_US is used. You may create your own language file here or edit existing ones, but keep in mind that if you create your own file it will not auto update with the newest messages if you install a newer version of the plugin.  

### playerparticles.db

This is the database file that will be used if you have MySQL disabled in the config.yml. If you are using MySQL, you can safely delete this file. Deleting this file with SQLite enabled will cause a loss of data saved for the plugin.