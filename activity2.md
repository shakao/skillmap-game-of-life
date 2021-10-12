# Game of Life Rules

## Step 1
To begin with, look at the game in the simulator.  

Notice that the population is as placed. To see what will come of the 
population, we need to introduce the concept of time to this population 
to view the future generations. 

## Step 2
The first rule that we'll be introducing is that **any live cell with two
or three live neighbors survives**.

[Gif of the situation]

## Step 3

The first step is to figure out how many neighbors around a cell are alive.
We've provided a function called "countAliveNeighbors" that takes in the 
column and row of a cell. Write code to return the number of neighbors 
that are alive. 

[maybe add block that is "for each direction"]

## Step 4 

Now use your function! In the "run generation" event, write the first rule:
if a cell has two or three alive neighbors, it will survive.

## Step 5 

Otherwise, the cell dies 

## Step 6 

If a dead cell, has exactly 3 alive neighbors, it becomes alive. 

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