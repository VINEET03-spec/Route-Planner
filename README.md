
# Route Planner

The Traveling Salesman Problem statement is as follows: Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city?
We want the shortest tour. It can’t be solved in polynomial time (NP-Hard) because suppose there are 19 cities, then I have 19 choices of which one to visit first, 18 choices of which one to visit second, …, 1 choice of which one to visit at last. In total, that’s 19! possibilities and if I have a computer that can test 1 billion tours per second, it will take 19! / 1,000,000,000 ~ 3.85 years to finish. Therefore, I will use Genetic Algorithm and Google Maps API to solve and visualize this problem.
Note that this project is solely built when the number of input cities is very large(at least 10).



The Traveling Salesman Problem (TSP) aims to find the shortest route that visits each city exactly once and returns to the starting city. Given its factorial complexity (N!), GA provides a heuristic approach by mimicking natural selection and genetics.



Let the No of cities or locations be N. 


First, we just randomly generate a sequence/array of cities to travel to. For example, [0,5,3,2,1,4] means we will travel to city 0 first, then city 5, then city 3, then city 2, then city 1, and finally city 4. We call this sequence/array an individual.

The current Population is nothing different, except we will have an array of individuals. This array is the population we want to breed and evolve. It has a size of popSize.


Calculate Fitness is the process of ranking/sorting the population based on each individual’s fitness. In TSP, an individual’s fitness is the total distance traveled.

Just like Darwin’s theory of natural selection (or survival of the fittest), we also want the individuals that have less total distance to survive. However, we just want them to be more likely to survive instead of entirely wiping out other individuals, this way we avoided converging to a local optimal solution too quickly.


Here is how to do this:


- Initially give each individual the same probability of being selected = 1/8
- Multiply the two fittest (shortest distance) individuals’ probability by 6
- Multiply the remaining top half of individuals’ probability by 3
- Normalize the probabilities.
Finally, it is time to generate our next population! We want to select pairs (i.e. 2 individuals) for popSize times so that the selected pair can “give birth to” a new individual (breeding). 

For the pairs selection part, we will simply generate a number between 0 and 1 called threshold. We start from 0, and accumulate as we walk through the Selection Chance array, whenever the current cumulative sum is ≥ threshold, we select the individual with the current index we are at, and we repeat this process another time to select two individuals.


Randomly decide whether parent A or parent B goes first
Randomly generate a crossover index from 1 to popSize — 2
- Copy cities from the first parent [0…crossover index]
- Copy any cites that aren’t already in the child from the second parent.
Finally, we should add the notion of mutation to increase a little bit more randomness to prevent early convergence. For this, we define a variable representing mutation chance mutChance. If we mutate, simply pick two random indices in the child and swap their values.

Once we have popSize children generated, we are going to replace the current population with the new population and be ready to move on to the next iteration. We will repeat all of the above numIterations times. 

After all iterations, we select the fittest individual in the final population as the solution.
