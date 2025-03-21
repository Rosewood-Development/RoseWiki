## Number Providers
RoseLoot currently has four different ways of getting numerical input from a loot table.  You can find each of the three options below.  It is fully supported to put a number provider within another number provider.  See the placeholders section at the bottom for an example of this.

### Constant Number
As simple as it gets, a constant number.  This value may or may not allow negative numbers or decimals, the value should specify what the valid numbers are.
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount: 1
```

### Uniform Distribution
If you want to pick a random number between a range with a uniform distribution, this is the number provider for you.  Randomly generated numbers are limited to 2 decimal places by default, this can be changed using the `decimals` property, use -1 for uncapped precision.
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount:
              min: 1
              max: 10
              decimals: 2
```

### Binomial Distribution
If you want to pick a random number but want it more weighted towards the center, this should help do what you want.  The value of `n` determines how many trials to run, and the value of `p` is the probability of a trial passing.  `p` should be a number between 0 and 1, 1 being a 100% chance of passing.  The example below will run 10 trials each with a 50% chance of passing.  The average will be the same value as the example in the uniform distribution (5) but will be more weighted towards the average.
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount:
              n: 10
              p: 0.5
```

### Placeholders
Want to use a placeholder value as a number instead?  Not a problem!  As long as a placeholder will return a numerical value, it will work here! 
```yaml
type: ENTITY
overwrite-existing: items
conditions:
  - 'entity-type:villager'
pools:
  0:
    conditions: []
    entries:
      0:
        conditions: []
        items:
          0:
            type: item
            item: emerald
            amount:
              min: '%player_health_rounded%'
              max: '%player_level%'
```