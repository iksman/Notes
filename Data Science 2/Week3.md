# Week 3 - Genetic Algorithms

## Intro

Heuretic means aproximately but not exactly.<br>
Some problems don't have exact solutions since the dataset may be too big, for example the ```traveling salesman problem```<br>

## Initialization

Possibilities:

* Randomly
* Previously saved population
* Set of solutions provided by human expert
* Set of solutions provided by another heuristic algorithm

## Fitness

Choosing fitness function:

* Silhouette
* If it is slow, the entire algorithm is slow (repeated a lot)
* Similair encoded solutions have similair fitness

## Selection

Who becomes parent? -> Survival of the highest fitness

* ```Roulette wheel selection```
* ```Tournament selection``` -> easiest
* ```Rank selection```

### Roulette Wheel Selection

Higher fitness = higher chance of selection.<br>
<b>Randomness</b> is introduced to combine parents with other parents and get clearer results<br>
<b>Drawback</b> is highest fitness almost always gets chosen

<b>Implementation:</b><br>

* Calculate weight by dividing fitness by total fitness. -> ```0.4, 0.3, 0.3```
* Calculate cumulative probability. -> ```0.4, 0.7, 1```
* Plot it on a line -> ```(0)-----(0.4)----(0.7)----(1)```
* Generate random floating point number between ```0``` and ```1``` -> ```0.8```

### Rank Selection

Higher fitness = selection<br>
<b>No randomness</b>, set values means better distribution<br>
<b>Drawback</b> is that there are no diverse outcomes

<b> Implementation: </b>

* Rank all the items by fitness
* Best fitness is highest number
* Worst fitness is lowest number
* Best fitness therefor is ```n``` where ```n``` is amount of items
* Worst fitness therefor is ```1```

### Tournament Selection

Running small "tournaments" among a few individuals chosen at random <br>
Winner of each tournament (one with the best fitness) is selected for crossover<br>

---

## Crossover
Many ways to perform a recombination, depends on the representation of individuals.

### Single Point Crossover

* One crossover point is selected
* Mix children by mixing before- and after of the parents on set point<br>```123|456, 987|654``` -> ```123654, 987456```

### Two Point Crossover

* Randomly two points are selected
* Mix children by selecting 2 points to go to the other parent while the other parent gives 1 point back to the first<br>```12|34|56, 98|76|54``` -> ```983454, 127656```

### Uniform Crossover

* Bits are randomly copied from the first and second parent<br>```123456, 987654``` -> ```187454, 923656```

### Arithmetic Crossover

* Some arithmetic operation is performed to make new offspring

---

## Mutation

<b>Random changes in the offspring</b> to simulate the effect of errors that happen with low probability.<br>
Used to prevent the falling of all solutions in the population into a local optimum

### Binary Encoding

* Invert a few randomly chosen bits from ```1``` to ```0``` or ```0``` to ```1```

---

## Elitism

When creating the new population, we could lose best indivuals.<br>
To avoid this, we can <b>copy the few best individuals directly</b> and always into the new population.<br>
This is done to prevent losing the best on every iteration and can increase performance of algorithm.

---

## Termination Condition

* The fitness hasn't changed in a number of iterations.
* Fixed amount of generations.

Randomness can't be used this time :^)

---

## Parameters values

General recommendations:

* <b>Crossover Rate</b> should be high: ~80% - 95%
* <b>Mutation Rate</b> should be very low: ~0.01% - 0.1% 
* <b>Population Size</b> should be ~20-30, best size depends on size of encoded string.
* <b> Selection: </b>
    * <b>Roulette Wheel</b> selection is a good choice
    * <b>Elitism</b> should be used
