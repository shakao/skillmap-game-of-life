### @explicitHints true

# Conway's Game of LIfe

## Artificial Intelligence @showdialog
You've probably heard a lot about AI, but how would you define 
Artificial Intelligence? One perspective is that it is an effort to 
create something which behaves like a living thing!  

![Gif of evolution of multiple Methuselahs](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/complex-life.gif)

Strikingly, it is possible to create a game from simple rules 
which exhibits basic features which we expect from living things. 
One such game is called Conway's Game of Life! The 'breathing' pattern above is one such Game of Life pattern.


##  Introduction

**Conway's Game of Life**, and the world it creates is incredibly rich, 
containing 'creatures' which can reproduce themselves, 
communicate and move, unpredictably evolve. The Game of Life can itself be used to 
create an entire computer 💻! 

- :mouse pointer: When you're ready to move on to the next set of instructions, click **Next**.

## 🕹️ Play the game

Open the game window to take a look at the Game of Life and **🕹️ try it**.
Try button **A** to pause and unpause. You can use button **B** to advance one step at a time.

When you're ready to continue, click into the instructions tab again!

Here we see a grid of cells, colored cell are 'alive' and black cells are 'dead' and cells 
next to one another can 'see' each other. Observe the game to see
the rich patterns evolve in time. Check out this 'striking' example which builds 'gliders' which impact another cluster of living cells.

![Gif of multiple pentadecathlon patterns in game of life](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/gospers-penta.gif)

✨ Experiment by changing the ``||conways:set initial state||`` block by clicking on grey box to produce your own intial state.
See how your initial state evolves in the game window!

#### ~ tutorialhint 

Try drawing a 'glider' which looks like this:

![Image of a glider](https://raw.githubusercontent.com/shakao/skillmap-game-of-life/master/images/glider.png)

## Rules 📜

This world evolves in time by only **three rules** crafted to make life-like behavior.

In the next few steps, you will see how **three rules** can create life-like 
evolution, and how missing any of these rules leads the simulation to break down. 


## Rule One 👪

We expect that life 🌱 needs life around it to survive. Humans need plants 
and plants need soil and so on. However too much life will leave 
some creatures without enough to eat 🥣. 

So the first rule is that after one generation of time, any live cell with **two 
or three neighboring live cells** survives to the next time. **More than 
3 live neighbors** means that cell may not have enough to eat or
space to live, and so that cell does not survive.

Now let's try turning this rule OFF in the editor.

- :paper plane: Delete the call to ``||Functions:rule one||`` to see how it breaks the world! 
Did you expect it to break this way? Without this rule there is no death or cooperation.

**🕹️ Play the game 🕹️**

- :paper plane: Add back the call to ``||Functions:rule one||`` block

_💡 You can use the undo button in the bottom tool bar to get back to the original code_

## Rule Two 👶

Life also creates life! The second rule for this world is that any dead cell 
which has **exactly 3 live neighbors** becomes alive! A small family can have 
children, but a large family may not have enough food to support more life! 

Now let's try turning this rule OFF.

- :paper plane: Delete the call to ``||Functions:rule two||`` this rule to see how it breaks 
the world. Without birth, how can life continue?

**🕹️ Play the game 🕹️**

- :paper plane: Add back the call to ``||Functions:rule two||`` block

## Rule Three ⚰️

Nothing in life lasts forever, and so our simulation must follow this as well.
The third rule is that any live cells not supported by neighbors will become
 dead, and that all dead cells which don't birth a new cell stay dead. 
 
 Now let's try turning this rule OFF.
 
- :paper plane: Delete the call to ``||Functions:rule three||``, which means live cells don't die! 

**🕹️ Play the game 🕹️**

- :paper plane: Add back the call to ``||Functions:rule three||`` block

## Finale


In the next tutorial you will build these rules yourself and understand in detail 
how to create a simulation of life 🌱! 

When you're done playing your game, click **Done** to return to the 
main skillmap for the next tutorial.


```ghost
conways.onGenerationUpdate(function (col, row) {
    neighbours = Functions.countAliveNeighbours(col, row)
    Functions.RuleOne(col, row, neighbours)
    Functions.RuleTwo(col, row, neighbours)
    Functions.RuleThree(col, row, neighbours)

    if (conways.getState(col, row)) {
        if (neibhours == 3) {
            conways.setState(col, row, false)
        }
    }
    if (conways.getIsDeadInDirection(conways.Direction, 0, 0)) {
            conways.setState(col, row, false)
    }
    if (conways.getStateInDirection(conways.Direction, 0, 0)) {
                conways.setState(col, row, false)
    }
    if (conways.getState(0, 0)) {
                conways.setState(col, row, false)
    }
    if (conways.getIsDead(0, 0)) {
            conways.setState(col, row, false)
    }
})

```

```customts
//% color="#1446A0"
namespace Functions {

export let ruleOneRan = false;

//% block
export function RuleOne (col: number, row: number, neibhours: number) {
    ruleOneRan = true;
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
    if (!ruleOneRan) {
        // do opposite of Rule1
        if (conways.getState(col, row)) {
            if (neibhours == 2) {
                conways.setState(col, row, false)
            } else if (neibhours == 3) {
                conways.setState(col, row, false)
            }
        }
    }
    ruleOneRan=false;
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

```template
conways.onGenerationUpdate(function (col, row) {
    let neighbours = Functions.countAliveNeighbours(col, row)
    Functions.RuleOne(col, row, neighbours)
    Functions.RuleTwo(col, row, neighbours)
    Functions.RuleThree(col, row, neighbours)
})
conways.setInitialState(img`
........................................
......................1.................
........................1...............
.....................11..111............
........................................
........................................
........................................
........................................
........................................
........................................
.............1..........................
.......11...............................
........1...111.........................
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
.........11.............................
........11..............................
.........1..............................
...................................11...
..................................11....
...................................1....
........................................
`
```

```package
arcade-conways=github:jwunderl/arcade-conways#v0.0.4
```
