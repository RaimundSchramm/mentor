# ROOD - Ruby Object Oriented Design

## Contents

- [Classes and Modules](#classes-and-modules)

-

### Classes and Modules

On one hand arranging code in any Model-View-Controller(MVC)-App can lead to a so-called God-Class. Using this approach leads to very few and on a file-and-path-level easily maintainable but codewise to huge, hard to read an maintainable parts.

On the other hand applying the Single Responsibility Principle(SRP) leads codewise to very readable and maintainable but on a file-and-path-level complex parts.

The target app will probably be something in between both extremes.

-

1. Find an object

Start by finding any object of interest from the domain you want to model.

1.1 Found Pyramids

Pyramids is an object that has the following static and dynamic behaviour:

static

- it is recognizable by its unique name and image
- it is referred to as a wonder and by a purple color
- it is of a certain age
- it is unique to a game
- it is a kind of building that is built in phases
  that each bind one blue token and cost resources and civil actions
- it provides a certain bonus to the player upon completion

dynamic

- it changes its position in a game
  - it is shuffled randomly into the civil deck of age A of a new game
  - it is drawn and put onto the game's cardrow
  - it is picked up by a certain player of this game or discarded
  - it is moved to this player's board

