# GAME OF CLASSES

We are going to create a turn-based battle game where two armies will face off in a simulation. Each army will consist of **five warriors**, each one from a **specific subclass**. The warriors will have unique attributes and abilities that differentiate them in combat.

# Requirements

## **Warrior Superclass**:

This will be the base class from which all types of warriors will inherit. Each warrior's attributes will be assigned randomly within a range defined by the specific subclass.

`Common attributes`:

- name (string): Warrior's name.
- health (int): Amount of health points. This value will be assigned randomly within a range, depending on the type of warrior.
- strength (int): Defines the attack power. Random value within a specific range.
- defense (int): Indicates how much damage the warrior can block.
- speed (int): Determines which warrior attacks first in a turn.

`Common methods`:
- attack(target): Performs an attack on another warrior. This method will be redefined in the subclasses.
- defend(damage): Reduces the damage taken based on the defense attribute.
- is_alive(): Returns True if the warrior's health is greater than 0, otherwise False.
- show_stats(): Displays the current attributes of the warrior.

## **Warrior Subclasses**:

Each subclass will have a specific range for health, strength, defense, and speed. The values will be randomly generated within these ranges when each warrior is instantiated. The methods `attack()` and `defend()` will also be customized for each subclass.

### `Knight`

`Attributes`:  
```  
    - health: Between 100 and 150.
    - strength: Between 30 and 40.
    - defense: Between 50 and 70.
    - speed: Between 10 and 20.
```

`Methods`:
- **attack**(target): The Knight performs a direct attack based on their strength.
***Damage formula: damage = strength * 1.2***
- **defend**(damage): The Knight blocks a percentage of the damage taken, based on their defense.
***Formula: damage_taken = damage - (defense * 0.6)***.

### `Archer`

`Attributes`:
```
    - health: Between 70 and 100.
    - strength: Between 25 and 35.
    - defense: Between 20 and 30.
    - speed: Between 40 and 60.
```
`Methods`:
- **attack**(target): The Archer has a 30% chance to perform an attack that ignores 50% of the opponent's defense.
***Normal damage formula: damage = strength * 1.0***.
***Special attack formula (30% chance): damage = strength * 1.0, but the target’s defense is halved.***
- **defend**(damage): There is a **20% chance** to completely evade the attack.
If not evaded, the damage taken is: ***damage_taken = damage - (defense * 0.4)***.

### `Mage`

`Attributes`:
```
    - health: Between 50 and 80.
    - strength: Between 40 and 60.
    - defense: Between 10 and 20.
    - speed: Between 20 and 30.
```
`Methods`:
- **attack**(target): The Mage has a 10% chance to cast a magical attack that affects all enemies instead of just one.
Single-target attack: ***damage = strength * 1.5 to one enemy.***
Massive attack: ***damage = strength * 0.8 to all enemies.***
- **defend**(damage): Has a 10% chance to dodge the attack and heal an ally for 15 health points.
If not dodged, the damage taken is: ***damage_taken = damage - (defense * 0.4)***.

### `Assassin`
`Attributes`:
```
    - health: Between 60 and 90.
    - strength: Between 35 and 45.
    - defense: Between 15 and 25.
    - speed: Between 50 and 70.
```
`Methods`:
- **attack**(target): Has a 25% chance to perform a critical hit that deals double damage.
***Normal attack formula: damage = strength * 1.0.***
***Critical attack formula: damage = strength * 2.0.***
- **defend**(damage): A 30% chance to avoid all damage. Otherwise, the damage taken is: ***damage_taken = damage - (defense * 0.15)***.

### `Healer`
`Attributes`:
```
    - health: Between 80 and 120.
    - strength: Between 10 and 20.
    - defense: Between 20 and 30.
    - speed: Between 30 and 40.
```

`Methods`:
- **attack**(target): The Healer performs a basic attack.
***Damage formula: damage = strength * 0.8.***
- **heal**(target): Instead of attacking, the Healer can heal themselves or an ally.
***Healing formula: heal = 30 health points.***
- **defend**(damage): Has magical defense that reduces the damage taken.
***Formula: damage_taken = damage - (defense * 0.5).***

## **Simulation Rules**

### 1 - Army Creation:

**Two armies** will be created, each made up of five warriors, one from **each subclass**.
Warrior attributes will be randomly generated within the established ranges.

### Turn-based Battle:

The army with the fastest warrior will attack first.

The order of turns within the same army is determined by the speed attribute of each warrior. The fastest warrior will attack first, followed by the slower ones.

Warriors will randomly choose an opponent to attack, or perform a specific action based on their subclass. (We can either let the player choose who to attack, decide the action based on the subclass, or make it random.)

Each turn, one warrior from each team will play sequentially. A warrior cannot attack twice before all their teammates have had at least one attack.

The simulation ends when all warriors in an army are defeated (health <= 0).

### Victory Condition:

The army with at least one surviving warrior will win the battle.

***TIP to prevent your code output from becoming too long, you can use the `clear_output` function from the IPython.display library.***

***Used like this: clear_output(wait=True) it will clear the output once there’s more text to display on the screen.***