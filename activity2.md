### @explicitHints true

# Game of Life

## Introduction 🧬

We saw in the previous tutorial that three rules were needed to 
build a simulation of life which features self-replication, 
communication and motion, and chaotic unpredictable patterns. 

These rules all basically require looking at each cell and 
counting how many live neighbors that cell has. 

Let's begin by writing code which counts alive neighbors! 

## Counting Neighbors

There is a function in your workspace that takes the **column** 
and **row** of a cell. Write code to return the number of alive 
neighbors for this cell.

#### ~ tutorialhint 

Think about how to add up the neighbors of the cell you're at! 
Maybe this block will help:

```block
if (conways.getStateInDirection(conways.Direction, 0, 0) {}
```

## Adding Rules

Now that we can count alive neighbors, we need to implement the 
three rules of Conway's Game of Life! We saw in the last tutorial 
that these rules are: 

1. Any live cell with 2 OR 3 living neighbors survives. 
2. Any dead cell with exactly 3 living neighbors becomes alive. 
3. All other live cells die, and all other dead cells stay dead. 

We've made a function for each of these rules. Look at the 
`||conways:on generation update [x] [y]||` block to see where they are being 
called! 

## Surviving Cells 

In the `||functions:ruleOne||` function, add code to
ensure that any **currently alive cell** with 2 or 3 living 
neighbors survives to the next generation. Make sure to use 
the `||functions:countAliveNeighbors||` function you just 
wrote!

[rule gif]

#### ~ tutorialhint 

```blocks
function ruleOne(col: number, row: number, neighbors: number) {
    if (conways.getState(col, row)) {
        if (neighbors == 2) {
            conways.setState(col, row, true);
        } else if (neighbors == 3) {
            conways.setState(col, row, true);
        }
    }
}
```

## New Cells

Next, add the `||functions:ruleTwo||` code so that any 
**currently dead cell** with exactly three living neighbors 
becomes alive.

[rule gif]

## Dying Cells ⚰

Finally, add the `||functions:ruleThree||` code so that any 
**currently alive cell** with less than two or greater than 
three living neighbors dies.  

[rule gif]

## Play the Game! 

Life starts with something! Here we've added for you a 'glider,' 
which is named by its ability to walk across the world in time. 

🕹 Check it out in the simulator tab. 🕹

Add in more blocks, try an oscillator, a 'gun', and more, and click 
"play" to see the evolution. Try pausing and moving one step at a 
time to see how the rules create the patterns! 


```ghost
let count = 0;
let north = conways.Direction.North;
if (conways.getState(0, 0) || conways.getIsDead(0, 0)) {
    if (conways.getStateInDirection(conways.Direction, 0, 0) 
        || conways.getIsDeadInDirection(conways.Direction, 0, 0)
        && count < 3) {
        count = count + 1;
        conways.setState(0, 0, false);
    }
}
let directions = [];
```

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
    return 0;
}

function ruleOne(col: number, row: number, neighbors: number) {
}

function ruleTwo(col: number, row: number, neighbors: number) {
}

function ruleThree(col: number, row: number, neighbors: number) {
}

conways.onGenerationUpdate(function(col: number, row: number) {
    let neighbors = countAliveNeighbors(col, row);
    ruleOne(col, row, neighbors);
    ruleTwo(col, row, neighbors);
    ruleThree(col, row, neighbors);
})
```

```customts
let paused = false;
game.onUpdateInterval(500, function () {
    if (!(paused)) {
        conways.nextGeneration()
    }
})
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
    conways.nextGeneration()
})
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    paused = !(paused)
})
```

```package
arcade-conways=github:jwunderl/arcade-conways#v0.0.4
```
