## Introduction
The permissions for PlayerParticles revolve around players having access to individual effects and styles. If they have the permission for an effect or style, they are able to use that effect or style. Access to use data is granted by default.

## Permissions Nodes

| Permission Node | Description | Suggested User Level |
| --- | --- | --- |
| playerparticles.basecommand | Grants permission to use `/pp`. | Any |
| playerparticles.effect.<name\> | Grants permission to use an effect. Negative permissions are supported. A list of available effects can be found [here](particle-details.md#effects). Replace `<name>` with the name of an effect. | Any |
| playerparticles.effect.* | Grants permission to use all effects. | Any |
| playerparticles.style.<name\> | Grants permission to use a style. Negative permissions are supported. A list of available styles can be found [here](particle-details.md#styles). Replace `<name>` with the name of a style. | Any |
| playerparticles.style.* | Grants permission to use all styles. | Any |
| playerparticles.fixed | Grants permission to use fixed effects with `/pp fixed`. | Trusted users |
| playerparticles.fixed.clear | Grants permission to use `/pp fixed clear`. | Admins |
| playerparticles.fixed.teleport | Grants permission to use `/pp fixed teleport`. | Admins |
| playerparticles.fixed.max.<number\> | Grants permission to use <number\> amount of fixed effects. | Trusted users |
| playerparticles.fixed.unlimited | Grants permission to use an unlimited amount of fixed effects, bypassing the value set in the config.yml. | Admins |
| playerparticles.particles.max.<number\> | Grants permission to have <number\> amount of particles applied at once. | Trusted users |
| playerparticles.particles.unlimited | Grants permission to have an unlimited number of particles applied at once, bypassing the value set in the config.yml. | Trusted users |
| playerparticles.groups.max.<number\> | Grants permission to have <number\> amount of groups saved. | Trusted users |
| playerparticles.groups.unlimited | Grants permission to have an unlimited number of groups saved, bypassing the value set in the config.yml. | Trusted users |
| playerparticles.gui | Grants permission to use `/pp gui`. This permission is disabled by default and can be enabled in the config.yml. | Any |
| playerparticles.reload | Grants permission to use `/pp reload`. | Admins |
| playerparticles.reset.others | Grants permission to use `/pp reset [player]`. | Admins |
| playerparticles.override | Grants permission to use `/ppo`. | Admins |
| playerparticles.worldguard.bypass | Allows bypassing WorldGuard region restrictions, if enabled | Trusted users |