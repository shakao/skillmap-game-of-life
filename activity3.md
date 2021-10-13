### @explicitHints true

# Conway's Game of Life Challenge Activity

## Introduction
We saw in the previous tutorial that the **three rules** are very important for the Game
of Life to behave in a life-life fashion. In this tutorial, let's take a look at how the initial life states produce
the rich patterns that emerge over time.

![Alt txt](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/gospers-penta.gif )

## Still Life Pattern
Can you find an initial state that stays **fixed** over time? ✋
- :paper plane: From the ``||conways:Life||`` category, modify the
``||conways:set initial state [] ||`` to put in an initial state.
- :paper plane: Use the editor to draw a pattern that would stay fixed over time.
- :paper plane: Now, go over to the game window to see 
the simulation in action for the progression of the future generations.
Is the initial population staying still?

#### ~ tutorialhint

Example still life pattern

![Alt txt](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/stillLife.png)

## Oscillator Pattern
Can you find an initial state that **oscillates** over time? 👆👇👆

_An oscillating pattern is one that comes back to its initial
state after a number of iterations._
- :paper plane: From the ``||conways:Life||`` category, modify the
``||conways:set initial state [] ||`` to put in an initial state.
- :paper plane: Use the editor to draw an initial state that would lead to oscillations.
- :paper plane: Now, go over to the game window to see 
the simulation in action for the progression of the future generations.
Does it come back to same state as the initial state after a number of generations?

#### ~ tutorialhint

Example oscillator pattern

![Alt txt](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/oscillator.png)

## Spaceship Pattern
Can you find an initial state that **moves itself across the grid** over time?
- :paper plane: From the ``||conways:Life||`` category, modify the
``||conways:set initial state [] ||`` to put in an initial state.
- :paper plane: Use the editor to draw a pattern that would be able to move across
the grid over time.
- :paper plane: Now, go over to the game window to see 
the simulation in action for the progression of the future generations.
Does it continue moving across the grid?

#### ~ tutorialhint

Example spaceship pattern

![Alt txt](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/glider.png)

## Grand Finale
You've done it! You've experienced Conway's Game of Life through this simulation
and seen that it is possible to create a game from simple rules which exhibits
basic features which we expect from living things. 

When you're done playing your game, click **Done** to return to the 
main skillmap. Congrats!

```template
conways.setInitialState(img`
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
......111.........111.........111.......
.......1...........1...........1........
.......1...........1...........1........
......111.........111.........111.......
........................................
......111.........111.........111.......
......111.........111.........111.......
........................................
......111.........111.........111.......
.......1...........1...........1........
.......1...........1...........1........
......111.........111.........111.......
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
........................................
`)

function countAliveNeighbors(col: number, row: number) {
    let count = -0
    if (conways.getStateInDirection(conways.Direction.North, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.NorthEast, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.East, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.SouthEast, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.South, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.SouthWest, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.West, col, row)) {
        count += 1;
    }
    if (conways.getStateInDirection(conways.Direction.NorthWest, col, row)) {
        count += 1;
    }
    return count
}

function ruleOne(col: number, row: number, neighbors: number) {
    if (conways.getState(col, row)) {
        if (neighbors == 2) {
            conways.setState(col, row, true)
        } else if (neighbors == 3) {
            conways.setState(col, row, true)
        }
    }
}

function ruleTwo(col: number, row: number, neighbors: number) {
    if (conways.getState(col, row) == false) {
        if (neighbors == 3) {
            conways.setState(col, row, true)
        }
    }
}

function ruleThree(col: number, row: number, neighbors: number) {
    if (conways.getState(col, row)) {
        if (neighbors < 2) {
            conways.setState(col, row, false)
        } else if (neighbors > 3) {
            conways.setState(col, row, false)
        }
    } 
}

conways.onGenerationUpdate(function(col: number, row: number) {
    let neighbors = countAliveNeighbors(col, row);
    ruleOne(col, row, neighbors);
    ruleTwo(col, row, neighbors);
    ruleThree(col, row, neighbors);
})
```

```customts
//% color="#1446A0"
namespace Functions {
//% block
export function RuleOne (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row)) {
        if (neibhours == 2) {
            conways.setState(col, row, true)
        } else if (neibhours == 3) {
            conways.setState(col, row, true)
        }
    }
}
//% block
export function RuleTwo (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row) == false) {
        if (neibhours == 3) {
            conways.setState(col, row, true)
        }
    }
}
//% block
export function RuleThree (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row)) {
        if (neibhours < 2) {
            conways.setState(col, row, false)
        } else if (neibhours > 3) {
            conways.setState(col, row, false)
        }
    } 
}
//% block
export function countAliveNeighbours (col: number, row: number) {
    let count = 0
    //Direction enum is from 0 to 7
    for (let i = 0; i < 8; i++) {
        if (conways.getStateInDirection(i, col, row)) {
            count += 1
        }
    }
    return count
}
}
let paused = false;
game.onUpdateInterval(100, function () {
    if (!(paused)) {
        conways.nextGeneration()
    }
})
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!paused) { 
        paused = true;
    }
    conways.nextGeneration()
})
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    paused = !(paused)
})
```

```package
arcade-conways=github:jwunderl/arcade-conways#v0.0.4
```

