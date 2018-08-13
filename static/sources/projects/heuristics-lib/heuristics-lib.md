layout: true
<div class="remark-header"><span><a href="" class="remark-quit-cross"><i class="fas fa-times fa-2x"></i></a></span></div>
<div class="remark-footer"><span>Meta Heuristics library<a href="" class="remark-icon-bottom"><i class="fas fa-times"></i></a><a href="" class="remark-icon-bottom"><i class="fas fa-times"></i></a></span></div>

---
class: center, middle
# Meta Heuristics library
<hr>
**Summary** : Implementation of operations research meta heuristics algorithms in C++ (Such as examples tabu search, simulated annealing, meta local search...)

---

# Description

The aim of the project is to offer some operations research metaheuristics for mono or multiple objectives problems. Used as a generic cpp library, this project can be improve for your own needs.

Into this library, for use Heuristic functions you have to declare your own fitness functions and if it's necessary your solution type based on Solution cpp class.

---

# Installation

If you just want to use this library, you can download sources code and import the library just as below :

```cpp
#include "metaheuristics.h"
```

Then, all features of this library are now available !

---

# Documentation

This library uses template C++ engine. A *Solution* class file is an abstract class with some virtual methods which need to be defined in any subclass.

---

## Create Solution

As explained the *Solution* class is the generic class which represents the solution of an optimisation problem.

*Solution* class represents your solution as an array of type **T**.

When you want to create your own solution you need to specify :

-   **swapIndex(int nb)** method : Method which represents a movement of your solution (if necessary).
-   **getNeighbors()** method : Method which returns all solutions considered as neighbors of your solution.


Below an example of how to create your own solution type :

```cpp
template<typename T>
class CombinatorySolution : public Solution<T> {

  /**
   * Method used for swap and permute index values (represents a movement)
   * @param nb : number of swap expected
   */
  void swapIndex(int nb){
    ...
  };

  /**
   * Method used for getting all neighbors solution of current solution
   * @tparam T : Template object Type, subclass of Solution
   * @param s
   * @return
   */
  vector<Solution<T>*>* getNeighbors(){
    ...
  };
}
```

---

## Local search

Into some metaheuristics you need to declare a local search algorithm to improve solution at each iteration. To make it generic a *Local* type is defined. Below the definition expected of this local search algorithm.

```cpp
typedef C* (Local)(int nbEvaluation, Heuristics<C> *heuristics, C* s);
```

If you want to declare your owns local search algorithm you need to respect this signature. Some famous local search are available into [LocalSearch.hpp](https://github.com/jbuisine/MetaHeuristicsLibrary/blob/master/src/algorithms/localsearch/LocalSearch.hpp) file as static methods.

Below an example of a metaheuristics which uses a local search algorithm.

```cpp
C* run(int nbEvaluation, int nbPerturbation, Local localSearch, int nbIterationLocal);
```

---

## Selector

Into some metaheuristics, especially for Evolutionary Algorithms, you want to select lambda solutions from mu population in order to generate your new population for next generation. With this library, you can used existing Selectors or your owns you have created. Below the definition expected of this selector function.

```cpp
typedef std::vector<int>* (Operator)(std::vector<double>* muScores, int lambda);
```

If you want to declare your owns selectors you need to respect this signature. Some famous selectors are available into [EASelectors.hpp](https://github.com/jbuisine/MetaHeuristicsLibrary/blob/master/src/algorithms/operators/EASelectors.hpp) file as static methods.

Below an example of a metaheuristics which uses selector.

```cpp
C* run(int mu, int lambda, int iteration, Selector selector, Local localSearch, int nbIterationLocal);
```

---

## Operator

Into some metaheuristics you want to change solution state by using such as example crossover operators, mutation operators. Especially for Evolutionary Algorithms, you can used existing Operator or your owns you have created. Below the definition expected of this operator function.

```cpp
typedef C* (Operator)(C* fstSol, C* sndSol);
```

If you want to declare your owns operators you need to respect this signature. Some famous operators are available into [EAOperators.hpp](https://github.com/jbuisine/MetaHeuristicsLibrary/blob/master/src/algorithms/operators/EAOperators.hpp) file as static methods.
Note that you can specify a method into Solution class which will be used dynamically into your Operator function using polymorphism (like used into EAOperators.hpp file).

Below an example of a metaheuristics which uses operators.

```cpp
C* run(int mu, int lambda, int iteration, Operator crossover, Operator mutation, Local localSearch, int nbIterationLocal);
```

---

## Fitness definition

Each solution of an optimisation problem are evaluated with a fitness to obtain the score of this solution. This library contains a fitness type :

```cpp
typedef double (*Fitness)(long);
```
The long parameter is used for retrieve the pointer of your solution.

You can declare your own fitness functions just like that :
```cpp
// Fitness example
double compute (long ptrToParam) {

    // Casting your pointer address into your solution type
    auto * s = (BinaryCombinatorySolution<int>*)ptrToParam;

    double score = 0.0;

    ....

    return score;
}
```

---

# Heuristics

*Heuristics* class is abstract class of each metaheuristics inherits. You can define your problem configuration when you create an instance of a subclass of *Heuristics*.

---

## Problem configuration

Constructor of *Heuristics* class permits you to defined your problem :

-   Your problem type (minimizing or maximizing problem).
-   Fitness function(s) (Mono or multi-objective problem).
-   Size of the solution of your problem.

The comments available into this piece of code explain again how to configure your problem :

```cpp
template<typename C>
class Heuristics {

public:
    /**
     * Initialization of context
     * @param problem_type : 'false' specify minimizing problem and 'true' maximizing
     * @param f : objective function(s)
     * @param s_size : size of problem solution
     */
    Heuristics(bool problem_type, vector<Fitness>& funcs, int size) {
        this->funcs = funcs;
        this->size = size;
        this->problem_type = problem_type;
    }     

    ...
};
```

---

## Utilities methods

Into *Heuristics* class usefull methods are developed to check solutions dominance.

-   
```
bool checkSolution(C* o, C* n)
```
    -   _**Description :**_ compare two solutions (old and new) dominance.
        -   *return false :* if new solution is better than the old solution.
        -   *return true  :* if new solution is worse than the old solution.
<br><br>
-     
```
bool checkSolution(vector<double>& scores, C* n)
```
    -   _**Description :**_ compare vector of a solution score for each fitness to another solution.
        -   *return false :* if new solution is better than solution already known.
        -   *return true  :* if new solution is worse than solution already known.
<br><br>
-         
```
vector<C*>* getNonDominatedSols(vector<C*>* sols)
```
    -   _**Description :**_ Only for multi objective problem, this method returns all non dominated solutions from a set of solutions.
        -   *return :* all non dominated solutions.

---

## Create your own metaheuristic

If you want to create your own metaheuristic class which contains multiple versions and implementations of a specific metaheuristics, you can create your own subclass of *Heuristics* class :

```
template<typename C>
class YourMetaHeuristic : public Heuristics<C> {
  ...
}
```

An important thing you need to do, is to define your new constructor based into the *Heuristics* constructor to initialize context problem.

```
YourMetaHeuristic(bool problem_type, vector<Fitness>& funcs, int size)
  : Heuristics<C>(problem_type, funcs, size){}
```

---

## Metaheuristics developed

### MetaLocalSearch

  - ```
    runMultiStart(int nbEvaluation, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Multi start local search implementation.
    <br><br>
  - ```
    runILS(int nbEvaluation, int nbPerturbation, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Iterated local search implementation.
    <br><br>
  - ```
    runDVN(C* solution, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Descent variable neighborhoods implementation.
    <br><br>
  - ```
    runSVNBase(int nbEvaluation, int kMax, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Search for variable neighborhoods base version.
    <br><br>
  - ```
    runSVNGeneral(int nbEvaluation, int kMax, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Search for variable neighborhoods general version (using DVN).
    <br><br>
  - ```
    runSVNReduce(int nbEvaluation, int kMax);
    ```
    <br>**Description** : Search for variable neighborhoods reduce version (without local search).
    <br><br>

---

### SimulatedAnnealing

  - ```
    run(int nbEvaluation, double temperature, double minTemperature, double alpha);
    ```
    <br>**Description** : Simulated annealing simple implementation.
    <br><br>

---

### MetaLocalSearch

  - ```
    runStrongMemory(int nbEvaluation, int nbMovement, int nbPerturbation);
    ```
    <br>**Description** : Tabu search implementation with strong memory.
    <br><br>
  - ```
    runAdaptableMemory(int nbEvaluation, int nbMovement, int nbPerturbation, int tabuCounter);
    ```
    <br>**Description** : Tabu search implementation with memory counter.
    <br><br>

---

### EvolutionaryAlgorithm

  - ```
    C* runSimple(int mu, int lambda, int iteration, Selector childrenSelector, Selector generationSelector, Operator crossover, Operator mutation, Local localSearch, int nbIterationLocal);
    ```
    <br>**Description** : Evolutionary Algorithm simple implementation using customized selectors, operators and local search.
    <br><br>

---
# Some examples
## Simulated annealing

Below an example of how you can throw a Simulated Annealing metaheuristic to solve your problem :

```cpp
// Constant declarations
const int NB_EVAL_PER_TEMP   = 10;
const double TEMPERATURE     = 300.0;
const double MIN_TEMPERATURE = 0.003;
const double DECREASE_FACTOR = 0.98;

int nbElements = 1000;

vector<Fitness> f;

// 'compute' is the defined fitness function
f.push_back((Fitness) compute);

// Maximazing problem with one objective function
auto *sa = new SimulatedAnnealing<BinaryCombinatorySolution<int>>(true, f, nbElements);

BinaryCombinatorySolution<int>* s =
  sa->run(NB_EVAL_PER_TEMP, TEMPERATURE, MIN_TEMPERATURE, DECREASE_FACTOR);

s->diplaySolution();
```

---

## Tabu search

Below an example of how you can throw a Tabu Search metaheuristic with adaptable memory to solve your problem :

```cpp
// Constant declarations
const int TABU_ITERATION = 1000;
const int NB_MOVEMENT = 10;
const int NB_PERTURBATION = 10;
const int TABU_COUNTER = 3;

int nbElements = 1000;

vector<Fitness> f;

// 'compute' is the defined fitness function
f.push_back((Fitness) compute);

// Maximazing problem with one objective function
auto *h = new TabuSearch<BinaryCombinatorySolution<int>>(true, f, nbElements);

BinaryCombinatorySolution<int>* s =
  h->runAdaptableMemory(TABU_ITERATION, NB_MOVEMENT, NB_PERTURBATION, TABU_COUNTER);

s->diplaySolution();
```

---

## QAP instance example

At the moment this library is usefull for QAP instance. An example of knapsack QAP instance is present into [ks_1000.txt](https://github.com/jbuisine/MetaHeuristicsLibrary/blob/master/resources/knapsack/ks_1000.txt) file.

An example of how to use this QAP instance with the Meta Heuristics library is available into [mainKnapsack.cpp](https://github.com/jbuisine/MetaHeuristicsLibrary/blob/master/src/mainKnapsack.cpp) file.

An implementation of current metaheuristics implemented are also available.

---

# Contribution

Contribution is **open** !

If you want to contribute, this project use cMake build tool so if you use an IDE which has cMake, you only have to load the project with.

Some metaheuristics have multiple versions with their own advantages for each specific kind of problem. If you see an alternative of one of these metaheuristics don't hesitate to fork this project and contribute to it ! It just wants to be enhanced !

---

# Conclusion

This library wants to become your operations research library for solving your optimisation problems. New metaheuristics can be found each day, this library aim is to propose an implementation of this discovery.

Meta Heuristic library project is now at version v0.2.4. Do not hesitate to give me feedback about another way we can imagine make this library to be more generic and adaptable.
