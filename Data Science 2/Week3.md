# Week 3

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