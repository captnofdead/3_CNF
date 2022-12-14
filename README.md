# 3_CNF

This Repository Contains the Code for 3_CNF SAT Solver Using Genetic algorithm. There are better algorithms that exist to solve the given problem, I tried to showcase the uses of Genetic algorithm as a searching algorithm. <br />

The algoithm generates a random population of N(here N = 40) candiates, each candidate being a list of x(variables in the CNF statement) number of binary values, then it follows the steps given below
* The algorithm performs the reproduction state, where it stochastically selects 2 parents to produce a child. for weights of the stochastic selection process, fitness value is used which is the number of clauses satisfied by the candidate.

* Each child is made by chosing a crossover point and appending the prefix of one parent and suffix of the other parent till the crossover point.

* After the reproduction stage, the old population is updated by this new population of children, and out of all the children the best fitness value child is compared to the global best candidate which is updated accordingly if needed.

* The algorithm performs the above three tasks until it runs out of the number of iterations or all the clauses of the CNF is satisfied.

## Optimizations

* Culling:
At the reproduction stage of our algorithm, instead of greedily selecting children, we store all of the children formed in a given generation and then stochastically select the remaining 75% of the population. This is an example of culling, which helps to avoid getting stuck in a local search area by avoiding greedy selection.
  
* Elitism:
In order to improve the accuracy of our algorithm, we have implemented elitism. This involves selecting the best 25% of parents, based on their fitness value, and passing them on to the next generation. By doing this, we are ensuring that our solution's high-performing segments are preserved. We have found that using a 25% elitism rate produces excellent results.

* Random Restarts
In addition to implementing elitism and culling, we have also incorporated the idea of a random restart. Suppose the maximum fitness value achieved by a generation is the same as the previous generation for 100 consecutive generations. In that case, we conclude that we are stuck at a local maximum in the search space. To escape this local maximum, we reset the population randomly. This improved the accuracy of the algorithm significantly. The new population is independent of the previous one, and the best solution found so far is stored in the `best_population` variable to ensure that it is not lost.
