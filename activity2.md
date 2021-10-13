# Game of Life

## Introduction

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

## Adding Rules

Now that we can count alive neighbors, we need to implement the 
three rules of Conway's Game of Life! We saw in the last tutorial 
that these rules are: 

1. Any live cell with 2 OR 3 living neighbors survives. 
2. Any dead cell with exactly 3 living neighbors becomes alive. 
3. All other live cells die, and all other dead cells stay dead. 

## Surviving Cells 

In the `||life:on generation [x] [y]||` block, add code to
ensure that any **currently alive cell** with 2 or 3 living 
neighbors survives to the next generation. 

[rule gif]

## New Cells

Next, add code so that any **currently dead cell** with exactly
three living neighbors becomes alive.

[rule gif]

## Dying Cells

Finally, add code so that any **currently alive cell** with less 
than two or greater than three living neighbors dies.  

[rule gif]

## Play the Game! 

Life starts with something! Here we've added for you a 'glider,' 
which is named by its ability to walk across the world in time. 
Check it out in the simulator tab.

Add in more blocks, try an oscillator, a 'gun', and more, and click 
"play" to see the evolution. Try pausing and moving one step at a 
time to see how the rules create the patterns! 


```ghost
let count = 0;
let north = life.direction();
if (life.getIsAlive(0, 0)) {
    if (life.getIsAliveDirection(life.Direction.North, 0, 0) && count < 3) {
        count = count + 1;
        life.setIsAlive(true, 0, 0)
    }
}
let directions = [];
```

```template
function countAliveNeighbors(x: number, y: number) {

}

game.onUpdate(function () {
	
})
```

```package
game-of-life-fake=github:shakao-test/game-of-life-fake#v0.0.2
```