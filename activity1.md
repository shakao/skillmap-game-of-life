# Conway's Game of LIfe

## Artificial Intelligence @showdialog
You've probably heard a lot about AI, but how would you define 
Artificial Intelligence? One perspective is that it is an effort to 
create something which behaves like a living thing!  

[TODO:Gif of the situation]

Strikingly, it is possible to create a game from simple rules 
which exhibits basic features which we expect from living things. One such game is called Conway's Game of Life!


##  Introduction

**Conway's Game of Life**, and the world it creates is incredibly rich, 
containing 'creatures' which can reproduce themselves, 
communication and motion, unpredictable evolution, and can itself be used to 
create an entire computer 💻! 

- :mouse pointer: When you're ready to move on to the next set of instructions, click **Next**.

## 🕹️ Play the game

Open the game window to take a look at the Game of Life and **🕹️ try it** 

When you're ready to continue, click into the instructions tab again!

Here we see a grid of cells, black is 'alive' and white is 'dead' and cells 
next to one another can 'see' each other. Observe the game to see
the rich patterns evolve in time. Try button **A** to pause and unpause. 
When paused you can use button **B** to step through one generation at a time. 

[TODO:Gif of the situation][See a penta-decathlon, a glider and a gun which eventually hits the pentadecathlon. ]

## Rules

This world evolves in time by only **three rules** crafted to make lifelike behavior.

In the next few steps, you will see how three rules 📜 can create lifelike
 evolution, and how missing any of these rules leads the simulation to break down. 


## Rule One 👪

We expect that life 🌱 needs life around it to survive. Humans need plants 
and plants need soil and so on. However too much life will leave 
some creatures without enough to eat 🥣. 

So the first rule is that after one generation of time, any live cell with two 
or three neighboring live cells survives to the next time. More than 
3 live neighbors means that cell may not have enough to eat or
space to live, and so that cell does not survive.

Try turning this rule OFF by [TODO: Add code to switch off] to see how it breaks the world! 
Did you expect it to break this way? Without this rule there is no death or cooperation. 

**🕹️ Play the game 🕹️**

## Rule Two 👶

Life also creates life! The second rule for this world is that any dead cell 
which has exactly 3 live neighbors becomes alive! A small family can have 
children, but a large family may not have enough to support more life! 

Now try turning OFF [TODO: Add code to switch off Rule 2] this rule to see how it breaks 
the world. Without birth, how can life continue? 

**🕹️ Play the game 🕹️**

## Rule Three ⚰️

Nothing in life lasts forever, and so our simulation must follow this as well.
The third rule is that any live cells not supported by neighbors will become
 dead, and that all dead cells which don't birth a new cell stay dead. 
 
 Now let's try turning this rule off [TODO: Add code to switch off Rule 2], which means live cells don't die! 

**🕹️ Play the game 🕹️**

## Finale


In the next tutorial you will build these rules yourself and understand in detail 
how to create a simulation of life 🌱! 

When you're done playing your game, click **Done** to return to the 
main skillmap for the next tutorial.


```ghost
conways.onGenerationUpdate(function (col, row) {
    neighbours = countAliveNeighbours(col, row)
    RuleOne(col, row, neighbours)
    RuleTwo(col, row, neighbours)
    RuleThree(col, row, neighbours)

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
//% block
function RuleOne (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row)) {
        if (neibhours == 2) {
            conways.setState(col, row, true)
        } else if (neibhours == 3) {
            conways.setState(col, row, true)
        }
    }
}
//% block
function RuleTwo (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row) == false) {
        if (neibhours == 3) {
            conways.setState(col, row, true)
        }
    }
}
//% block
function RuleThree (col: number, row: number, neibhours: number) {
    if (conways.getState(col, row)) {
        if (neibhours < 2) {
            conways.setState(col, row, false)
        } else if (neibhours > 3) {
            conways.setState(col, row, false)
        }
    } 
}
//% block
function countAliveNeighbours (col: number, row: number) {
    let count = 0
    //Direction enum is from 0 to 7
    for (let i = 0; i < 8; i++) {
        if (conways.getStateInDirection(i, col, row)) {
            count += 1
        }
    }
    return count
}
let paused = false;
game.onUpdateInterval(500, function () {
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
    let neighbours = countAliveNeighbours(col, row)
    RuleOne(col, row, neighbours)
    RuleTwo(col, row, neighbours)
    RuleThree(col, row, neighbours)
})
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
`
```

```package
arcade-conways=github:jwunderl/arcade-conways#v0.0.4
```
