# 3_CNF

This Repository Contains the Code for 3_CNF SAT Solver Using Genetic algorithm. There are better algorithms that exist to solve the given problem, I tried to showcase the uses of Genetic algorithm as a searching algorithm. <br />

The algoithm generates a random population of N(here N = 40) candiates, each candidate being a list of x(variables in the CNF statement) number of binary values, then it follows the steps given below
* The algorithm performs the reproduction state, where it stochastically selects 2 parents to produce a child. for weights of the stochastic selection process, fitness value is used which is the number of clauses satisfied by the candidate.

* Each child is made by chosing a crossover point and appending the prefix of one parent and suffix of the other parent till the crossover point.

* After the reproduction stage, the old population is updated by this new population of children, and out of all the children the best fitness value child is compared to the global best candidate which is updated accordingly if needed.

* The algorithm performs the above three tasks until it runs out of the number of iterations or all the clauses of the CNF is satisfied.

## Optimizations

* Culling:
  
* Elitism

* Random Restarts

