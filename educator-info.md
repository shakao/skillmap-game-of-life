# A Game of Life

The [Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) (or Life, simply) is a simple rule-based cellular automaton designed by British mathematician John Conway in 1970. It is not a real game in the sense that once the “initial state” is specified, the subsequent iterations are automatic based upon the rules of the game. In that sense it is a zero-player game. The evolution of the game’s patterns can grow to produce interesting objects which self-replicate, move, and communicate. The patterns can even be contrived so that the Game of Life itself simulates an entire computer! The takeaway message is that endless complexity can arise from simple rules and that these life-like automata, being a model of life, can even [model](https://en.wikipedia.org/wiki/Universal_Turing_machine) the [programmed intelligence of a computer](https://www.youtube.com/watch?v=Kk2MH9O4pXY). In that sense they can be considered an early effort to understand Artificial Intelligence.

The rules of the game are simple. The world is a grid of cells (like pixels), wherein a cell can be on (alive) or off (dead). The rules cover concepts of birth, death, and survival. A live cell (ON cell) with two or three live neighbors survives; any dead cell with three live neighbors comes back to life; All other living cells die in the next generation as dead cells stay dead.

Starting with a seed pattern, the game evolves applying the above rules in each generation which is an iteration of the game. A generation is the application of these set of rules to the board. A simulation is a series of applications of the rules, leading to striking patterns across generations.

## What do students learn?

In this game, students learn about cellular automaton which are basically rows or groups of cells with simple rules that govern birth, and death and survival of cells based on simple rules. The starting pattern determines how the pattern grows and splits and [stabilizes across generations](https://www.youtube.com/watch?v=r46Oiq5Za6A). A nice starting pattern would be an R-Pentomino which consists of five alive cells arranged as shown:

![An r-pentomino shape on a grid](/images/r-pentomino.png)

This seemingly basic pattern ultimately requires over 1000 generations to stabilize and has many progeny patterns including oscillators, still-life, and gliders (which are the colorful names researchers have given to describe many patterns in the Game of Life).

One can start with a grid and randomly turn cells on or off, observing the evolution of the patterns. Is there any way to develop intuition for how the patterns will evolve? Are they predictable? It turns out the Game of Life is “[undecidable](https://en.wikipedia.org/wiki/Decidability_(logic))” which means that there is no computer program which can ‘decide’ whether some pattern will eventually arise from a given starting point.

The basic concept students learn is how to simulate evolution automatically based upon basic rules of the Game of Life. The students will start by turning off individual rules to see how essential each one is for complex evolution to occur. Without cooperation there can be no survival, without birth no life, without death, a static crystal of life appears. The game is finely tuned to be complex!

The students then implement the logical elements of the rules of the Game of Life, starting by writing a function which computes the number of alive neighbors of a cell. With this function, the rules can be programmed with a few logical if-statements. Once the students have implemented this, they can play with the simulation, adding new initial states, and building an intuition for the rich behavior. Finally, the students explore the taxonomies of the ‘life’ in Game of Life, finding ‘oscillators’, ‘still-life’, ‘gliders’, and ‘guns.’

## Links and resources
- [John Conway on how he created The Game of Life](https://www.youtube.com/watch?v=R9Plq-D1gEk)
- [Stephen Hawking "The Meaning of Life" segment on the Game of Life](https://www.youtube.com/watch?v=CgOcEZinQ2I)
- [Life in life! (the game of life being using to simulate… the game of life](https://www.youtube.com/watch?v=xP5-iIeKXE8)
- [A digital clock implemented in the Game of Life](https://www.youtube.com/watch?v=3NDAZ5g4EuU)