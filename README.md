# 3_CNF

This repository contains code for a 3-CNF SAT solver using a genetic algorithm. While there may be better algorithms for solving this problem, this implementation aims to demonstrate the use of a genetic algorithm as a search technique. <br />
The algorithm begins by generating a random population of N candidates (where N=40 in this case), with each candidate representing a list of binary values for the variables in the CNF statement. The algorithm then follows the steps described below:

* The algorithm performs the reproduction stage, where it stochastically selects two parents to produce a child. The fitness value, which is the number of clauses satisfied by the candidate, is used as the weight for the stochastic selection process.
* Each child is created by choosing a crossover point and combining the prefix of one parent with the suffix of the other parent up to that point.
* After the reproduction stage, the old population is updated with the new population of children. The child with the best fitness value is compared to the global best candidate, and the global best is updated if needed.
* The algorithm repeats these steps until it reaches the maximum number of iterations or all clauses in the CNF statement are satisfied.

## Optimizations

* ***Culling***:
At the reproduction stage of our algorithm, instead of greedily selecting children, we store all of the children formed in a given generation and then stochastically select the remaining 75% of the population. This is an example of culling, which helps to avoid getting stuck in a local search area by avoiding greedy selection.
  
* ***Elitism***:
In order to improve the accuracy of our algorithm, we have implemented elitism. This involves selecting the best 25% of parents, based on their fitness value, and passing them on to the next generation. By doing this, we are ensuring that our solution's high-performing segments are preserved. We have found that using a 25% elitism rate produces excellent results.

* ***Random Restarts***:
In addition to implementing elitism and culling, we have also incorporated the idea of a random restart. Suppose the maximum fitness value achieved by a generation is the same as the previous generation for 100 consecutive generations. In that case, we conclude that we are stuck at a local maximum in the search space. To escape this local maximum, we reset the population randomly. This improved the accuracy of the algorithm significantly. The new population is independent of the previous one, and the best solution found so far is stored in the `best_population` variable to ensure that it is not lost.

## Observations
As the sentence's size increases, the problem's complexity also increases, causing the genetic algorithm to take longer to converge. It is also less likely for the algorithm to reach 100% accuracy for larger sentences, as it becomes more probable for clauses to be self-conflicting and, therefore, unsatisfiable. The number of local maxima also increases with the size of the sentence, making it more likely for the algorithm to get stuck in a local maximum. Even with the implementation of a random restart, it is not guaranteed that the algorithm will escape local maxima, as the search space grows rapidly with the number of clauses. Additionally, the number of models with high fitness values decreases due to the presence of conflicting clauses.
