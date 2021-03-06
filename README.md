# Tournament Utilities
This is a handful of utility classes for handling group generation, seeding etc. for match-play tournaments

## ArenaSelector
Pretty naive arena selector. Input an array of arenas and the amount of times each have been played and an array of available arenas (each arena must be an object that implements a `getArenaId` method). The selector will pick a random arena that hasn't been played before or failing that the least played arena of the available ones. Example in `example/ArenaSelector`.

## BalancedArena
A random-optimized arena pairing. Given a list of player pairings and a list of how often they have played each arena it will try any number of random combinations (1000 iterations is default) and present the most balanced selection of arenas (i.e. players are playing arenas they have played the least). You can also specify how many arenas to pick for each group. Example in `example/BalancedArena`.

## Simple pairing classes

See detailed descriptions of these pairing systems at: [http://senseis.xmp.net/?GroupPairing](http://senseis.xmp.net/?GroupPairing)

#### AdjacentPairing
Input an array of seeded players and it'll pair the strongest players together. Seed #1 will play Seed #2, Seed #3 will play seed #4 and so on. Returns an associative array with `groups` and `byes`. Set `group_size` to `4` to generate four-player groups. The bye will always go to the last seed. Example in `example/AdjacentPairing`.

#### CrossPairing
Input an array of seeded players and it'll dive the field into two halves pairing the strongest player from the top half with the strongest player from the bottom half. With 14 players Seed #1 will play Seed #8, Seed #2 will play Seed #9 and so on. Returns an associative array with `groups` and `byes`. The bye will always go to the last seed. Example in `example/CrossPairing`.

#### SlaughterPairing
Input an array of seeded players and it'll pair the strongest player with the weakest player. With 14 players Seed #1 will player Seed #14, Seed #2 will play Seed #13 and so on. Returns an associative array with `groups` and `byes`. Set `group_size` to `4` to generate four-player groups. The bye will always go to the last seed. Example in `example/SlaughterPairing`.

#### RoundRobinPairing
Input an array of players and it'll provide a RoundRobin pairing where each player plays every opponent once. Set the `double` option to true for Double RoundRobing pairings where every player plays each opponent twice. Example in `example/RoundRobinPairing`.

## More complex pairing classes

#### SingleEliminationBracket
Helper class for working with single elimination brackets. Relies on a binary heap structure as described in [http://joenoodles.com/2013/3/2013-bracket-design](http://joenoodles.com/2013/3/2013-bracket-design). Example in `example/SingleEliminationBracket`.

#### BalancedPairing
A random-optimized player pairing for either head-to-head or group play. Given a list of players and a list of how often they have played each other it will try any number of random combinations (1000 iterations is default) and present the most balanced solution (i.e. the solution where the fewest repeat opponents are present). Example in `example/BalancedPairing`.

#### HeadToHeadSwissPairing
A somewhat balanced head to head pairing. Takes an array of sub-groups with players and will match up players within in sub-group. Will make a naive attempt at matching players that have played each other the least. Example in `example/HeadToHeadSwissPairing`.

#### GroupTieredSwissPairing
Input an array of seeded players and it'll generate 4 player groups based on your seeds and a predefined map of increasingly smaller tiers (so players will be playing opponents at roughly their own level). Just like Pinburgh. Example in `example/GroupTieredSwissPairing` or go to [http://seeder.slapsave.com/](http://seeder.slapsave.com/)
