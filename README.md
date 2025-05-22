# DofusGA

__[Start DofusGA](https://fontaineriant.github.io/dofusga/voici/render/dofusga.html)__

DofusGA is a build optimizer for Dofus.

It's a powerful engine that uses a genetic algorithm to find the best items to equip given a use case, and runs 100% in the browser.

DofusGA optimizes for builds that will __win__ a fight where two characters are hitting each other. Finding the build that deals the most damage is easy. But how much sustainability are you willing to lose for it? Are crits worth losing a bit of power? You have resists but would it be better if they were about equal? Do you get more from a 12th AP or extra power?

DofusGA puts everything in the balance:
 * Stats, power and crits
 * Vitality, melee, ranged and elemental resistances
 * Critical and pushback resistances
 * AP/MP parry and wisdom
 * Opponent resistances
 * And more...

## Pameters

### Hard constraints
Set the minimum AP/MP/Range including or excluding exotics and the pool of items to consider.

The Tank variable will determine how high your resistances need to be. 0% means you don't expect to ever take damage,
100% means you expect to take exactly as much damage as you deal, typically for a 1v1 duel where both opponents are melee.
DofusGA will optimize for you to __win__ and winning doesn't always involve dealing a lot of damage.

If you absolutely want an item to be part of the build, like a legendary item or a particular weapon,
you can include it in core items. The more items are included, the faster and more accurate the results.
You can also blacklist items that work against your strategy or that you can't afford.

### Opponent resistances
Mostly useful to prioritize neutral damage over earth damage, pushback damage over elemental damage, non-critical over critical.

An interesting use cas is setting Neutral to 10% and Earth 30% on strenth pvp builds, then add Ebony Dofus damage lines below (or other "best element" spells). DofusGA will try to make strength builds that trigger the dofus' neutral damage rather than earth damage (unless the cost on other stats is too high).

Set everything to 0% for PvE builds.

### Lines to optimize
Include damage and healing lines for an average turn.

Use a negative weight if the damage is to a teammate. Use fractional weights to optimize a spell that you only use every other turn.

Example for a fire Pandawa who wants a balance of healing and damage:


| Line | Element | Base damage | Can crit | Crit damage | Crit % | Is weapon | Is ranged | Heals | Weight |
| :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- |
| Pandjiu × 2 (28 - 32 base damage) | Fire | 30 | ✓ | 36 | 10 | ✕ | ✓ | ✕ |  2 |
| Ebony Dofus (best element) | Best | 15 | ✕ |  |  | ✕ | ✓ | ✕ |  1 |
| Possessed Hammer (damage) | Neutral | 16.5 | ✓ | 20.5 | 20 | ✓ | ✕ | ✕ | -1 |
| Possessed Hammer (healing) | Fire | 16.5 | ✓ | 20.5 | 20 | ✓ | ✕ | ✓ | 3 |

