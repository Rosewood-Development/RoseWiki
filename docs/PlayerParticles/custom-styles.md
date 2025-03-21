## Introduction
If you would like to develop custom styles for use in the plugin, you can do so through the use of the API. The following is an example plugin to spawn an orb of particles to spin around the player.

## Creating a class that implements [ParticleStyle](https://github.com/Esophose/PlayerParticles/blob/master/src/main/java/dev/esophose/playerparticles/styles/ParticleStyle.java)
```java
public class ExampleParticleStyle implements ParticleStyle {

    private int step = 0;
    private final int maxStep = 20;
    private final double radius = 1.25;
    private final int amount = 5;
    private final double spread = 0.1;
    private final double speed = 0.05;

    @Override
    public List<PParticle> getParticles(ParticlePair particle, Location location) {
        List<PParticle> particles = new ArrayList<>();

        double angle = Math.PI * 2 * (this.step / (double) this.maxStep);
        double x = Math.cos(angle) * this.radius;
        double z = Math.sin(angle) * this.radius;
        Location point = location.clone().add(x, 0, z);

        for (int i = 0; i < this.amount; i++)
            particles.add(new PParticle(point, this.spread, this.spread, this.spread, this.speed));

        return particles;
    }

    @Override
    public void updateTimers() {
        this.step = (this.step + 1) % this.maxStep;
    }

    @Override
    public boolean isEnabled() {
        return true;
    }

    @Override
    public String getInternalName() {
        return "test";
    }

    @Override
    public Material getGuiIconMaterial() {
        return Material.EMERALD;
    }

    @Override
    public boolean canBeFixed() {
        return true;
    }

    @Override
    public boolean canToggleWithMovement() {
        return true;
    }

    @Override
    public double getFixedEffectOffset() {
        return 0;
    }

}
```
If you want users to be able to change the name of the style, you can pass the custom name through the default `getName()` method. Otherwise, just return `getInternalName()` instead. For consistency, it is recommended that you make the name contain lowercase characters only. Do not use spaces, as it will cause things to break. For more details about what each of the methods do, you can view the javadocs at the link provided above.

## Registering the style
```java
public class ExamplePlugin extends JavaPlugin implements Listener {
    private static final ParticleStyle EXAMPLE_STYLE = new ExampleParticleStyle();

    @Override
    public void onEnable() {
        Bukkit.getPluginManager().registerEvents(this, this);
    }

    @EventHandler
    public void onParticleStyleRegistration(ParticleStyleRegistrationEvent event) {
        event.registerStyle(EXAMPLE_STYLE);
    }
}
```
If you need to reference the custom style later, store an instance of it in a variable. There is no need to ever create more than one instance. If you don't want the style to run on the normal update loop, you can register it with `ParticleStyleRegistrationEvent#registerEventStyle(ParticleStyle)`. If you do this, you will need to spawn the particles manually. This is only recommended if you are going to be spawning particles based on an event in the world, such as a player teleporting. If you use an event, make sure to register it yourself, the API will not do it for you. An example of how to make an event-based style can be found [here](https://github.com/Esophose/PlayerParticles/blob/master/src/main/java/dev/esophose/playerparticles/styles/ParticleStyleMove.java).