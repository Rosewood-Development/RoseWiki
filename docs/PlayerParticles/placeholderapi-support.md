## Introduction
There are two different uses for PlaceholderAPI in PlayerParticles. The first is using the custom placeholders that PlayerParticles provides, which can be found below. The second is the ability to use any placeholder in any message in PlayerParticles. These messages can be edited in your locale file.

## Placeholders

| Placeholder | Description |
| --- | --- |
| %playerparticles_active_amount% | The active number of particles a player has applied. |
| %playerparticles_group_amount% | The number of groups that a player has saved. |
| %playerparticles_fixed_amount% | The number of fixed effects that a player has saved. |
| %playerparticles_is_moving% | `true` or `false` based on if the player is moving or not. |
| %playerparticles_is_in_combat% | `true` or `false` based on if the player is in combat or not. |
| %playerparticles_is_in_allowed_region% | `true` or `false` based on if the player is in an allowed region or not. |
| %playerparticles_can_see_particles% | `true` or `false` based on if the player has particle visibility toggled on or off. |
| %playerparticles_particle_effect_<#>% | Gets the name of an effect of a player's active particle with an ID. Replace <#> with the desired ID. |
| %playerparticles_particle_style_<#>% | Gets the name of a style of a player's active particle with an ID. Replace <#> with the desired ID. |
| %playerparticles_particle_data_<#>% | Gets the data of a player's active particle with an ID. Replace <#> with the desired ID. |
| %playerparticles_has_effect_<effect\>% | Checks if a player has a specific effect equipped. Replace <effect\> with the desired effect name. |
| %playerparticles_has_style_<style\>% | Checks if a player has a specific style equipped. Replace <style\> with the desired style name. |
